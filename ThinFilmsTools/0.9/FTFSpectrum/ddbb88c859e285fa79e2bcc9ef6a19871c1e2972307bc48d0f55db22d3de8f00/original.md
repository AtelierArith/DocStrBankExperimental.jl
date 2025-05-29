```
Normalize the experimental reflectance dividing by the reference reflectance and
multiplying by the theoretical one. The experimental and the reference reflectances
must have the same scale.

    R = normalize_reflectance(λ, Rexp, Rthe, Rref)

        λ: wavelength of interest [nm]
        Rexp: 2-columns array with wavelength in first one and experimental
            reflectance in the second
        Rthe: 2-columns array with wavelength in first one and theoretical
            reflectance in the second
        Rref: 2-columns array with wavelength in first one and reference reflectance
            in the second

The output has the same scale as the theoretical reflectance with the same length as λ.
```
