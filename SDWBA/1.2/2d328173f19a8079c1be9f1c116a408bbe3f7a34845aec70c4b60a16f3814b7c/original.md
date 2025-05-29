Calculate backscatter over a range of frequencies.  The insonifying sound comes from above (i.e., traveling in the -z direction).

#### Parameters

  * `s` : Scatterer object
  * `freq1`, `freq2` : Endpoints of the angle range to calculate.
  * `sound_speed` : Sound speed in the surrounding medium
  * `n` : Number of frequencies to calculate; defaults to 100

Returns: A dictionary containing elements "freqs", "sigma_bs", and "TS", 	each a length-n vector.
