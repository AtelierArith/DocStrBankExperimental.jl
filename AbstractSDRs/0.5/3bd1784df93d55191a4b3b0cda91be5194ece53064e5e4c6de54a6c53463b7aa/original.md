Receive nbSamples from the SDR and fill them in the output buffer. The buffer format depends on the SDR backend

# –- Syntax

  * buffer = recv(radio, nbSamples)

# –- Input parameters

  * radio : SDR object
  * nbSamples : Desired number of samples

# –- Output parameters

  * buffer : Output buffer from the radio filled with nbSamples samples
