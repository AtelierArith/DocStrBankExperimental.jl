Open a Software Defined Radio of backend 'type', tune accordingly based on input parameters and use the supported keywords. It returns a radio object, depending on the type of SDR that can be used with all AbstractSDRs supported functions

# –- Syntax

radio = openSDR(type,carrierFreq,samplingRate,gain,antenna;key)

# –- Input parameters

  * type  : Desired SDR type. The different supported radio format can be obtained with getSupportedSDR();
  * carrierFreq : Carrier frequency [Hz]
  * samplingRate : Sampling frequency (Hz)
  * gain : Analog Rx gain (dB)

# –- Output parameters

  * radio : Defined SDR object
