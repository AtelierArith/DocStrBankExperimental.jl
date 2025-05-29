Update gain of current radio device, and update radio object with the new obtained gain. If the input is a [UHDRx] or a [UHDTx] object, it updates only the Rx or Tx gain

# –- Syntax

updateGain!(radio,gain)

# –- Input parameters

  * radio	  : SDR device
  * gain	: New desired gain

# –- Output parameters

  * gain : New gain value
