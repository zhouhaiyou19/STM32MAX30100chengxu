# STM32 MAX30100 程序

## 简介

本仓库提供了一个基于STM32的MAX30100程序，用于读取和处理血氧和心率数据。MAX30100是一款集成了光电容积脉搏波描记器（PPG）和心率监测功能的高精度传感器。

## 功能描述

程序的主要功能包括：

- 初始化延时函数
- 设置NVIC中断分组
- 初始化串口通信
- 初始化LED端口
- 初始化按键连接的硬件接口
- 初始化定时器
- 初始化IIC通信
- 初始化血氧传感器
- 循环更新FIFO数据，获取血氧和心率数据

## 主要代码

```c
int main(void) {
    delay_init();       // 延时函数初始化
        NVIC_PriorityGroupConfig(NVIC_PriorityGroup_2); // 设置NVIC中断分组2:2位抢占优先级，2位响应优先级
            uart_init(115200);  // 串口初始化为115200
                LED_Init();        // LED端口初始化
                    KEY_Init();          // 初始化与按键连接的硬件接口
                        TIM3_Int_Init(100-1720-1); // 定时器初始化
                            IIC_Init();
                                SPO2_Init();
                                    while(1) {
                                            POupdate(); // 更新FIFO数据 血氧数据 心率数据
                                                    delay_ms(10);
                                                        }
                                                        }
                                                        ```

                                                        ## 使用方法

                                                        1. 克隆本仓库到本地：
                                                            ```sh
                                                                git clone https://github.com/your-repo/stm32-max30100.git
                                                                    ```

                                                                    2. 使用STM32开发环境（如Keil uVision）打开项目文件。

                                                                    3. 根据硬件连接，配置相关引脚和参数。

                                                                    4. 编译并下载程序到STM32开发板。

                                                                    5. 运行程序，观察串口输出或LED指示，获取血氧和心率数据。

                                                                    ## 硬件连接

                                                                    请根据MAX30100传感器的数据手册和STM32开发板的引脚定义，正确连接IIC接口和其他必要的硬件接口。

                                                                    ## 贡献

                                                                    欢迎提交Issue和Pull Request，共同完善本项目。

                                                                    ## 许可证

                                                                    本项目采用[MIT许可证](LICENSE)。

                                                                    ## 下载链接
                                                                    [STM32MAX30100程序](https://pan.quark.cn/s/89401da1d333) 

                                                                    (备用: [备用下载](https://pan.baidu.com/s/13ehpsF_DdN5PiN62evgNvA?pwd=1234))

                                                                    ## 说明

                                                                    该仓库仅用于学习交流，请勿用于商业用途。
