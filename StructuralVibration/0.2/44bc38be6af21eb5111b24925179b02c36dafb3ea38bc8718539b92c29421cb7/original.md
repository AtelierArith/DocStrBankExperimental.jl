```
modefreq(model::Plate, fmax)
modefreq(model::Membrane, fmax)
```

Computes the natural frequencies of a simply supported rectangular plate or a clamped rectangular membrane up to fmax

**Inputs**

  * `model`: Structure containing the data related to the plate
  * `fmax`: Maximum frequency for calculating the modal shapes [Hz]

**Outputs**

  * `ωmn`: Natural frequencies calculated up to ωmax = 2π*fmax [Hz]
  * `kmn`: Matrix of modal wave numbers
