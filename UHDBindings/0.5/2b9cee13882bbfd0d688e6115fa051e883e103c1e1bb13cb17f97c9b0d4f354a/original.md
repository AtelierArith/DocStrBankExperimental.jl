Update carrier frequency of current radio device, and update radio object with the new obtained carrier frequency. If the input parameter is the UHDBinding object, the desired carrier frequency will be applied on both Rx and Tx sides.  If the input is a [UHDRx] or a [UHDTx] object, it updates only the Rx or Tx carrier frequency   

# –- Syntax

updateCarrierFreq!(radio,carrierFreq)

# –- Input parameters

  * radio	  : UHD device [Union{UHDBinding,UHDRx,UHDTx}]
  * carrierFreq	: New desired carrier frequency
  * chan : Channel index to use (default 0)

# –- Output parameters

  * 
