```
MultiBandPhotosyntheticallyActiveRadiation{F, FN, K, E, C, SPAR, SPARD}
```

Light attenuation model with multiple wave length bands where each band (i) is attenuated like:

```
∂PARᵢ(z)/∂z = PARᵢ(kʷ(i) + χ(i)Chl(z)ᵉ⁽ⁱ⁾)
```

Where kʷ(i) is the band specific water attenuation coefficient, e(i) the chlorophyll exponent, and χ(i) the chlorophyll attenuation coefficient.

When the fields are called with `biogeochemical_auxiliary_fields` an additional field named `PAR` is also returned which is a sum of the bands.
