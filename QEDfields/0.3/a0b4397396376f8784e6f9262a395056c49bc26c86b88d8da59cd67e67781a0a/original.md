```
amplitude(field::AbstractPulsedPlaneWaveField, pol::AbstractDefinitePolarization, phi)
```

Returns the value of the amplitude for a given polarization direction and phase variable `phi`. 

!!! note "Conventions"
    There are two directions supported:

    ```Julia
    pol::PolX # -> return envelope(phi)*cos(phi)
    pol::PolY # -> return envelope(phi)*sin(phi)
    ```


!!! note "Safe implementation"
    In this function, a domain check is performed, i.e. if `phi` is in the domain of the field, the value of the amplitude is returned, and zero otherwise.

