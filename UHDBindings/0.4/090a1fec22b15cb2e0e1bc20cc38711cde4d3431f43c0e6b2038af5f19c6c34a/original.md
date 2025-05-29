Calling UHD function wrapper to fill a buffer. It is preferable to cal this function though the use of recv or recv!

# –- Syntax

recv!(sig,radio,nbSamples)

# –- Input parameters

  * radio	  	: UHD object [UHDRx]
  * ptr  		: Writable memory position [Ref{Ptr{Cvoid}}]
  * nbSamples : Number of samples to acquire

# –- Output parameters

  * nbSamp 	: Number of samples fill in buffer [Csize_t]
