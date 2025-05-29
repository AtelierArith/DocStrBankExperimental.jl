Init the core parameter of the radio in Tx or in Rx mode and initiate RF parameters 

# –- Syntax

openUHD(mode,sysImage,carrierFreq,samplingRate,txGain,antenna="RX2")

# –- Input parameters

  * mode 			: String to open radio in "Tx" (transmitter) or in "Rx" (receive) mode
  * carrierFreq	: Desired Carrier frequency [Union{Int,Float64}]
  * samplingRate	: Desired bandwidth [Union{Int,Float64}]
  * gain		: Desired Gain [Union{Int,Float64}]
  * antenna		: Desired Antenna alias Dict{Symbol,Vector[String]} (e.g. Dict(:Rx=>["RX2"],:Tx=>["TRX"]))

Keywords=

  * args	  : String with the additionnal load parameters (for instance, path to the FPHGA image) [String]

# –- Output parameters

  * uhd		  	: UHD object [UHDBinding]
