```
excitation(type, t)
```

Computes different types of excitation signals

**Inputs**

  * type : Excitation type

    1. `Triangle`
    2. `Rectangle`
    3. `Hammer`
    4. `SmoothRect`
    5. `SineWave`
    6. `HalfSine`
    7. `HaverSine`
    8. `SweptSine`
    9. `GaussianPulse`
    10. `ColoredNoise`
  * `t`: Time vector

**Output**

  * `F`: Excitation signal
