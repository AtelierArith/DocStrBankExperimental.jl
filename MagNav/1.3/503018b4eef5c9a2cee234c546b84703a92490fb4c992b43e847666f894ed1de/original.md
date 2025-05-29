```
psd(mapS::Union{MapS,MapSd,MapS3D})
```

Power spectral density of a potential field (i.e., magnetic anomaly field) map. Uses the Fast Fourier Transform to determine the spectral energy distribution across the radial wavenumbers (spatial frequencies) in the Fourier transform.

**Arguments:**

  * `mapS`: `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct

**Returns:**

  * `map_psd`: `ny` x `nx` power spectral density of 2D gridded map data
  * `kx`:      `ny` x `nx` x-direction radial wavenumber
  * `ky`:      `ny` x `nx` y-direction radial wavenumber
