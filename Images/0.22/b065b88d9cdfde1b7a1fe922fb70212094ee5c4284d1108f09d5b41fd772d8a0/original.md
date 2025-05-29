```
phantom = shepp_logan(N,[M]; highContrast=true)
```

output the NxM Shepp-Logan phantom, which is a standard test image usually used for comparing image reconstruction algorithms in the field of computed tomography (CT) and magnetic resonance imaging (MRI). If the argument M is omitted, the phantom is of size NxN. When setting the keyword argument `highConstrast` to false, the CT version of the phantom is created. Otherwise, the high contrast MRI version is calculated.
