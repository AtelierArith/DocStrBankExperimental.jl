Update gain of current radio device, and update radio object with the new obtained gain. If the input parameter is the UHDBinding object, the desired gain will be applied on both Rx and Tx sides.  If the input is a [UHDRx] or a [UHDTx] object, it updates only the Rx or Tx gain   

# –- Syntax

updateGain!(radio,gain)

# –- Input parameters

  * radio	  : UHD device [Union{UHDBinding,UHDRx,UHDTx}]
  * gain	: New desired gain
  * chan : Channel index to use (default 0)

# –- Output parameters

  * 
