```
reorganisation_energy(J::AbstractSD)
```

Calculate the reorganization energy of a given spectral density `J`, i.e.

$$
\int_0^\infty \frac{J(\omega)}{\omega} \mathrm{d}\omega 
$$

# Arguments

  * `J::AbstractSD`: The spectral density.

# Returns

  * The reorganization energy of the spectral density `J`.
