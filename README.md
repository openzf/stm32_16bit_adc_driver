ADS1115

ADS1115 is a 16bits Analog to Digital Converter

The ADS1115 is a 4-Channel Analog to Digital Converter

this lib is ADS1115 drive for stm32f103



how to use it ?

you only to  add the bsp_ads1115.c and  bsp_ads1115.h to  keil5 Project

then Init in the main function, and use GetAds1115Values function to get adc values,

for eg, use printf to show data in Serial port . and you can see there is anything else! 0.125???

    int main()
    { 
      printf_init();	
      ads1115_Init();
      
      while (1)
      {
        printf("%f\r\n",GetAds1115Values()*0.125);
      }
      
    }

why adc values Multiply 0.125?

the ads1115 has vref insdide chip ,so we don't like others Converter use   " 3.3/4096"

the values from GetAds1115Values function is inside values ,if it  Multiply gain_coefficient t,then the realValues is coming !

you can change it in  bsp_ads1115.c 

this list is GAIN with GAIN_COEFFICIENT

    typedef enum
    {
      GAIN_TWOTHIRDS    = ADS1015_REG_CONFIG_PGA_6_144V,  // 0.1875mV
      GAIN_ONE          = ADS1015_REG_CONFIG_PGA_4_096V,  // 0.125mV
      GAIN_TWO          = ADS1015_REG_CONFIG_PGA_2_048V,  // 0.0625mV
      GAIN_FOUR         = ADS1015_REG_CONFIG_PGA_1_024V,  // 0.03125mV
      GAIN_EIGHT        = ADS1015_REG_CONFIG_PGA_0_512V,  // 0.015625mV
      GAIN_SIXTEEN      = ADS1015_REG_CONFIG_PGA_0_256V  //  0.0078125mV
    } adsGain_t;
    






