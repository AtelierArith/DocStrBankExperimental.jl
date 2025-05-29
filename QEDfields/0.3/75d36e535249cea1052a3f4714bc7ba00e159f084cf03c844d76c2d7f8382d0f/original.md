```
generic_spectrum(field::AbstractPulsedPlaneWaveField, pol::AbstractDefinitePolarization, pnum)
```

Return the generic spectrum of the given field, for the given polarization direction `pol` and a given photon number parameter `pnum`.

!!! note "Convention"
    The generic spectrum is defined as the Fourier transform of the respective amplitude function for the given polarization direction:

    $$
    \begin{align*}
        x-\mathrm{pol} &\to \int_{-\infty}^{\infty} g(\phi) \cos(\phi) \exp(il\phi)\\
        y-\mathrm{pol} &\to \int_{-\infty}^{\infty} g(\phi) \sin(\phi) \exp(il\phi)
    \end{align*}
    $$

    where $g(\phi)$ is the [`envelope`](@ref) and $l$ the photon number parameter.

