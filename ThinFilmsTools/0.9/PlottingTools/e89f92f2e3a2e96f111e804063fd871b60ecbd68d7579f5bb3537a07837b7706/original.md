```
Plots the photonic dispersion (Bloch wavevector) of a photonic crystal structure,
computed for a range of frequencies (wavelengths) and one angle of incidence.

Takes one polarisation type in complex format, and plots on the left the imaginary
part and on the right the real part.

    plot(PBGDispersion1Dimre(), Bloch; s=(640,480))
    gui()

        solution.Bloch: Bloch structure of the solution
        wave: either p-wave (:p, default) or s-wave (:s)
            s: size of the figure
```
