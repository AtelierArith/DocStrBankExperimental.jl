```
oscillator(pol::AbstractPolarizaion, phi::Real)
```

Return the value of the base oscillator associated with a given polarization `pol` at a given point `phi`.

!!! note "Convention"
    The current default implementation are 

    ```Julia
    PolX() -> cos(phi)
    PolY() -> sin(phi)
    AllPol() -> (cos(phi), sin(phi))
    ```

