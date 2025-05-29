Send a buffer though the radio device. It is possible to force a cyclic buffer send (the radio uninterruply send the same buffer) by setting the cyclic parameter to true

# –- Syntax

send(radio,buffer,cyclic=false)

# –- Input parameters

  * radio	  	: UHD device [UHDRx]
  * buffer 	: Buffer to be send [Union{Array{Complex{Cfloat}},Array{Cfloat}}]
  * cyclic 	: Send same buffer multiple times (default false) [Bool]

# –- Output parameters

  * nbEch 	: Number of samples effectively send [Csize_t]. It corresponds to the number of complex samples sent.
