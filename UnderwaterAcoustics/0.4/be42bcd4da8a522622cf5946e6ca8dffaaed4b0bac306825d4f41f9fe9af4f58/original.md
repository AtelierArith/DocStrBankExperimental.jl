```
acoustic_field(pm::PekerisRayTracer, tx, rxs; mode=:coherent)
```

Compute the acoustic field at a receiver `rxs` due to a transmitter `tx` in the Pekeris waveguide. The field is computed incoherently if `mode=:incoherent`. Otherwise, the field is computed coherently.
