```
Optimize the parameters of the thin films in a multilayer stack using the selected models and the experimental spectrum.

    sol = fit_tmm_optics(
        specType, xinit, beam, Rexp, layers;
        order=1:length(layers), options=Optim.Options(), alg=SAMIN(),
        lb=0.5.*xinit, ub=1.5.*xinit, σ=ones(size(Xexp)), alpha=false,
        oftype=MeanAbs(),
    )

        specType: Type of spectrum to fit, with accepted values:
            Reflectance(Xexp), Transmittance(Xexp) or Ellipsometry(Xexp).
            For the Reflectance() and Transmittance() you must pass the spectrum array
            Xexp (0<=Xexp<=1) to be fitted. For the Ellipsometry() you have to
            pass the Ψ (first column) and Δ (second column) spectra in degrees, i.e.,
            Xexp = [Ψ Δ].
        xinit: Array with the initial parameters for optimization. For instance, to
            optimise two layers in the system you need to wrap the seeds for the
            algorithm as follow: xinit = [seed1, seed2], even if it is only one
            single layer to fit, xinit = [seed1]. The first parameter of each seed
            must be always the thickness, the rest are the parameters for the selected
            model. The number of seeds must match that of the number of ModelFit layers.
        beam: Structure from PlaneWave.
        layers: Columnwise array of LayerTMMO and ModelFit with information about the
            layers.
            order: Set the order of the layers (build the system) with the layers.
                This parameter is directly bound to the (previously defined) layers
                parameter. Order basically contains the indices of each layer inside
                the parameter layers. Notice that the first and last indices in
                order cannot be associated to ModelFit layers, as they are the
                outter media.
            options: Optional Optim.Options structure.
            alg: Optional algorithm method selected, by default takes SAMIN().
                You can pass the options inside as well, for instance, SAMIN(rt=0.1).
                Right now, LBFGS(), NelderMead() and SAMIN() are supported from
                Optim.jl. If you select SAMIN() you need to input lb and ub, otherwise
                will be set as 0.5 and 1.5 times the xinit argument, respectively.
                The LBFGS algorithm requires the jacobian for the optimisation but it
                can be omitted and the algorithm will calculate the differentials
                numerically.
            lb: Lower bounds for the optimisation variables, by default lb=0.5.*xinit
            ub: Upper bounds for the optimisation variables, by default ub=1.5.*xinit
            σ: Array with the standard deviation of the spectrum for each wavelength,
               by default is ones(size(Xexp)).
            alpha: Tells the procedure to either use (alpha=true) a linear decrease in
                the thicknesses of the modelling layers or not (alpha=false). The
                default is false, do not use alpha.
            oftype: Metric for the objective function to optimise.
                Can take values: MeanAbs() (default), SumAbs() and SumMeanAbs().

        sol: FitTMMOptics structure with results, with fields
            OptimSolverInfo: Status info from the solver
            spectrumFit: Spectrum obtained with the model and the optimal parameters
            spectrumExp: Input experimental spectrum
            optParams: Array of arrays with optimal parameters
            objfunMin: Optimum value of objective function MSE
            beam: Structure of the light used
            fitOptions: NamedTuple with information of the fitting procedure
```
