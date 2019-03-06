# Microcontroller feature
- STM32L073RZT6 in LQFP64 package
- ARM32-bit Cortex-M0+ CPU
- 32 MHz max CPU frequency
- VDD from 1.65 V to 3.6 V
- 192 KB Flash.
- 20 KB SRAM
- General purpose Timers (4) 
- Basic Timers (2)
- Low-power Timer
- SPI (2)
- I2S
- I2C (3)
- USART (4) 
- USB 2.0 full speed
- 12-bit ADC with 16 channels.
- 12-bit DAC(2) with 1 channel each.
- Comparators (2)
- RTC

# Architecture software

![architecture](https://user-images.githubusercontent.com/47490501/53897306-724df980-4068-11e9-89ba-7227a091d2eb.PNG)

1. Driver layers
This level is divided into three sub-layers:
+ Board Support package (BSP): this layer offers a set of APIs related to hardware components on the hardware boards
+ Hardware Abstract Layer(HAL): HAL peripheral drivers, Low layer drivers whch provide generic multi-instance feature-oriented APIs which simplyfy user application implementation by providing ready to use process. As example, for the communication peripheral (I2S, UART ..) its provides APIs allowing initializing and configuring the peripheral, managing data transfer base on polling, interrupt or DMA process, and handling communication errors that may raise during communication
The HAL driver APIs are split in two categories:
- Generic APIs which provides common and generic function to all the STM32 series.
- Extension APIs which provides specific and customized function for a specific family or a specific part number.
+ Basic peripheral usage example.

2. Middleware Layer
The middleware is a set of libraries covering USB Host and Device Libraries, FreeRTOS and FatFS. Horizontal interaction between the components of this layer is done directly by calling the feature APIs while the vertical interaction with the low-level drivers is done through specific callback and static marcos implemented in the library system call interface. For example, the FatFs implements the disk I/O driver to access microSD drive or the USB Mass Storage Class.

3. Application Layer
This level is composed of a single layer which consist in a global real-time and graphical demonstration based on the middleware service layer, the low-level abstraction layer and the basic peripheral usage application for board based features.
