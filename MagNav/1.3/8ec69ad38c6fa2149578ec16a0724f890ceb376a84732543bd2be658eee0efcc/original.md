```
psd(map_map::Matrix, dx, dy)
```

Power spectral density of a potential field (i.e., magnetic anomaly field) map. Uses the Fast Fourier Transform to determine the spectral energy distribution across the radial wavenumbers (spatial frequencies) in the Fourier transform.

**Arguments:**

  * `map_map`: `ny` x `nx` 2D gridded map data
  * `dx`:      x-direction map step size [m]
  * `dy`:      y-direction map step size [m]

**Returns:**

  * `map_psd`: `ny` x `nx` power spectral density of 2D gridded map data
  * `kx`:      `ny` x `nx` x-direction radial wavenumber
  * `ky`:      `ny` x `nx` y-direction radial wavenumber
