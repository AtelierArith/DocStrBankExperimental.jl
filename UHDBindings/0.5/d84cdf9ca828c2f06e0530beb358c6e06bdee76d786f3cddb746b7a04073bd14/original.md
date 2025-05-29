Get a single buffer from the USRP device, and create all the necessary ressources

# –- Syntax

sig	  = recv(radio,nbSamples)

# –- Input parameters

  * radio	  : UHD object [UHDRx]
  * nbSamples : Desired number of samples [Int]

# –- Output parameters

  * sig	  : baseband signal from radio [Array{Complex{CFloat}},radio.packetSize]
