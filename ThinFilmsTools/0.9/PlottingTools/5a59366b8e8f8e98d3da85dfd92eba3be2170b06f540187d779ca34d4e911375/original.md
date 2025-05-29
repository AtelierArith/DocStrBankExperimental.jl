```
Plots the index of refraction ath certain wavelength (usually λ0) of the multilayer
structure.

    plot(RIprofile(),
         solution;
         wave=:b, λ=solution.Misc.λ0, θ=solution.Beam.θ[1], s=(640,480),
    )
    gui()

        solution: structure solution from TMMOptics
            wave = :b (both, default), :p (p-wave), :s (s-wave) of the EMF to overlap
            θ: angle for which to overlap the EMF, by default is taken the first one
            λ: wavelength for which to overlap the EMF, by default is taken the reference one
            s: size of the figure
```
