```
upward_fft(map_map::Matrix, dx, dy, dz; expand::Bool = true, α = 0)
```

Upward continuation of a potential field (i.e., magnetic anomaly field) map. Uses the Fast Fourier Transform (FFT) to convert the map to the frequency domain, applies an upward continuation filter, and uses the inverse FFT to convert the map back to the spatial domain. Optionally expands the map temporarily with periodic padding. Downward continuation may be performed to a limited degree as well, but be careful, as this is generally unstable and amplifies high frequencies (i.e., noise).

Reference: Blakely, Potential Theory in Gravity and Magnetic Applications, 2009, Chapter 12 & Appendix B (pg. 315-317 & 402).

**Arguments:**

  * `map_map`: `ny` x `nx` 2D gridded map data
  * `dx`:      x-direction map step size [m]
  * `dy`:      y-direction map step size [m]
  * `dz`:      `nz` z-direction upward/downward continuation distance(s) [m]
  * `expand`:  (optional) if true, expand map temporarily to reduce edge effects
  * `α`:       (optional) regularization parameter for downward continuation

**Returns:**

  * `map_map`: `ny` x `nx` (x `nz`) 2D or 3D gridded map data, upward/downward continued
