Calculate backscatter over a range of angles.

#### Parameters

  * `s` : Scatterer object
  * `angle1`, `angle2` : Endpoints of the angle range to calculate.
  * `k` : Acoustic wavenumber vector
  * `n` : Number of angles to calculate; defaults to 100

#### Returns

A dictionary containing elements "angles", "sigma_bs", and "TS", each a length-n vector.
