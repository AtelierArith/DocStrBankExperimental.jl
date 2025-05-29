Update sampling rate of current radio device, and update radio object with the new obtained sampling frequency. If the input parameter is the UHDBinding object, the desired sampling frequency will be applied on both Rx and Tx sides.  If the input is a [UHDRx] or a [UHDTx] object, it updates only the Rx or Tx sampling frequency   

# –- Syntax

updateSamplingRate!(radio,samplingRate,chan=0)

# –- Input parameters

  * radio	  : UHD device [Union{UHDBinding,UHDRx,UHDTx}]
  * samplingRate	: New desired sampling rate
  * chan : Channel index to use (default 0)

# –- Output parameters

  * 
