Open a uhdOverNetwork remote device and initialize the sockets  –- Syntax

openUhdOverNetwork(carrierFreq,samplingRate,gain,antenna="RX2";ip="192.168.10.11")

# –- Input parameters

  * carrierFreq	: Desired Carrier frequency [Union{Int,Float64}]
  * samplingRate	: Desired bandwidth [Union{Int,Float64}]
  * gain		: Desired Rx Gain [Union{Int,Float64}]

Keywords 

  * ip	  : uhdOverNetwork IP address
  * antenna		: Desired Antenna alias  (default "TX-RX") [String]

# –- Output parameters

  * structuhdOverNetwork    : Structure with uhdOverNetwork parameters [SDROverNetwork]
