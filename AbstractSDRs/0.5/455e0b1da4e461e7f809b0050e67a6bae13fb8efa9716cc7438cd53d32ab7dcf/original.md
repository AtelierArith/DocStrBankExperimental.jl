Returns the radio packet size. Each radio backend encapsulates the IQ samples into chunks of data. The `recv` command can be used with any size but it can be more efficient to match the desired size with the one provided by the radio 

# –- Syntax

bufferSize = getBufferSize(radio) 

# –- Input parameters

  * radio	  : SDR device

# –- Output parameters

bufferSize : Size of radio internal buffer 
