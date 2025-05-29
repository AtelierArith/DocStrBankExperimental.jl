```
getMotionFreq(bSF::MPIFile, bMeas::MPIFile, choosePeak::Int)
```

Determines frequency [Hz] of signal modulation for each patch and frame

...

  * `bSF::MPIFile`: Systemfunction ==> required because the motion frequency is only determined from components with high SNR
  * `bMeas::MPIFile`: measurement
  * `choosePeak::Int`: Within the measurement signal different modulations can be found and also higher harmonics.

Choose the number of the peak you want ...
