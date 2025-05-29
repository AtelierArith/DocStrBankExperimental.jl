```
Computes the solution space for a window range of two parameters, the optical thickness
and porosity. Only works with these two parameters and for a single layer between
incident and emergent media.

    sol = space_solution_ema(specType, b, beam, Xexp, layers; oftype=MeanAbs())

        specType: Type of spectrum to fit, with accepted values:
            Reflectance(Xexp), Transmittance(Xexp) or Ellipsometry(Xexp).
            For the Reflectance() and Transmittance() you must pass the spectrum array
            Xexp (between 0 and 1) to be fitted. For the Ellipsometry() you have to
            pass the Ψ (first column) and Δ (second column) spectra in degrees.
        b: lower and upper boundaries for the optical thickness and porosity.
           (e.g. [odl, odu, pl pu; Nod, Np]), where Nod and Np indicates the number of
           points to search in the solution space as optional parameters.
        beam: structure from PlaneWave
        layers: columnwise array of three LayerTMMO and ModelFit with information
            about the layers. For space_solution_ema: length(vec(layers)) = 3. Notice that
            the type of the first and third layers is LayerTMMO while the type of the
            second layers is ModelFit.
            oftype: Metric for the objective function to optimise.
                Can take values: MeanAbs() (default), SumAbs() and SumMeanAbs().
        sol: structure with the solution
            solSpace: matrix with objective function values for the whole space
            objfunMin: minimum value of the objective function found
            optOD: optimum value of optical thickness
            optParams: optimum value of the other parameter
            optThickness: optimum value of thickness
            spectrumFit: optimum spectrum obtained with dopt and xopt
            spectrumExp: experimental spectrum
            od: range of optical thicknesses explored
            p: range of porosities explored
            beam: information of the light used
```
