```
Plots the photonic dispersion (Bloch wavevector) of a photonic crystal structure,
computed for a range of frequencies (wavelengths) and a range of angle of incidences.

This function plots the Bloch wavevector for only one of the polarisation types.

    plot(PBGDispersion2D(), solution.Bloch; wave=:p, s=(640,480), num_levels=90)
    gui()

        solution.Bloch: solution.Bloch structure from TMMOptics
            wave: either :p (p-wave, default) or :s (s-wave)
            s: size of the figure
```
