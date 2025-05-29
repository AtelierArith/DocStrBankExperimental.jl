```
Plots the photonic dispersion (Bloch wavevector) of a photonic crystal structure,
computed for a range of frequencies (wavelengths) and one angle of incidence.

Takes both polarisation types and renders them into one piece. You need to pass either
the real or imaginary parts of them.

    plot(PBGDispersion1Dalt(), Bloch; kpart=:real, s=(640,480))
    gui()

        solution.Bloch: Bloch structure of the solution
        kpart: either real (:real, default) or imginary (:imag)
            s: size of the figure
```
