```
Plots the photonic dispersion (Bloch wavevector) of a photonic crystal structure,
computed for a range of frequencies (wavelengths) and one angle of incidence.

Takes only one polarisation. If you want you can pass optionally the part of the
wavevector to plot. By default, plots the real one (as the imaginary does not represent
much).

    plot(PBGDispersion1D(), solution.Bloch; wave=:p, kpart=:real, s=(640,480))
    gui()

        solution.Bloch: Bloch structure of the solution
            wave: either p-wave (:p, default) or s-wave (:s)
            kpart: either real (:real, default) or imginary (:imag)
            s: size of the figure
```
