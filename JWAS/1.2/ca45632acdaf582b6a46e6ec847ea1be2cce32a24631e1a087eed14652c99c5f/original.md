```
runMCMC(model::MME,df::DataFrame;
        #Data
        heterogeneous_residuals           = false,
        #MCMC
        chain_length::Integer             = 100,
        starting_value                    = false,
        burnin::Integer                   = 0,
        output_samples_frequency::Integer = chain_length>1000 ? div(chain_length,1000) : 1,
        update_priors_frequency::Integer  = 0,
        #Methods
        estimate_variance               = true,
        single_step_analysis            = false, #parameters for single-step analysis
        pedigree                        = false, #parameters for single-step analysis
        fitting_J_vector                = true,  #parameters for single-step analysis
        categorical_trait               = false,
        censored_trait                  = false,
        causal_structure                = false,
        mega_trait                      = false,
        missing_phenotypes              = true,
        constraint                      = false,
        #Genomic Prediction
        outputEBV                       = true,
        output_heritability             = true,
        prediction_equation             = false,
        #MISC
        seed                            = false,
        printout_model_info             = true,
        printout_frequency              = chain_length+1,
        big_memory                      = false,
        double_precision                = false,
        ##MCMC samples (defaut to marker effects and hyperparametes (variance components))
        output_folder                     = "results",
        output_samples_for_all_parameters = false,
        ##for deprecated JWAS
        methods                         = "conventional (no markers)",
        Pi                              = 0.0,
        estimatePi                      = false,
        estimateScale                   = false)
```

**Run MCMC for Bayesian Linear Mixed Models with or without estimation of variance components.**

  * Markov chain Monte Carlo

      * The first `burnin` iterations are discarded at the beginning of a MCMC chain of length `chain_length`.
      * Save MCMC samples every `output_samples_frequency` iterations, defaulting to `chain_length/1000`, to a folder `output_folder`, defaulting to `results`. MCMC samples for hyperparametes (variance componets) and marker effects are saved by default. MCMC samples for location parametes can be saved using function `output_MCMC_samples()`. Note that saving MCMC samples too frequently slows down the computation.
      * The `starting_value` can be provided as a vector for all location parameteres and marker effects, defaulting to `0.0`s. The order of starting values for location parameters and marker effects should be the order of location parameters in the Mixed Model Equation for all traits (This can be obtained by getNames(model)) and then markers for all traits (all markers for trait 1 then all markers for trait 2...).
      * Miscellaneous Options

          * Priors are updated every `update_priors_frequency` iterations, defaulting to `0`.
  * Methods

      * Single step analysis is allowed if `single_step_analysis` = `true` and `pedigree` is provided.
      * Variance components are estimated if `estimate_variance`=true, defaulting to `true`.
      * Miscellaneous Options

          * Missing phenotypes are allowed in multi-trait analysis with `missing_phenotypes`=true, defaulting to `true`.
          * Catogorical Traits are allowed if `categorical_trait`=true, defaulting to `false`. Phenotypes should be coded as 1,2,3...
          * Censored traits are allowed if the upper bounds are provided in `censored_trait` as an array, and lower bounds are provided as phenotypes.
          * If `constraint`=true, defaulting to `false`, constrain residual covariances between traits to be zeros.
          * If `causal_structure` is provided, e.g., causal_structure = [0.0 0.0 0.0;1.0 0.0 0.0;1.0 0.0 0.0] for trait 1 -> trait 2 and trait 1 -> trait 3 (column index affacts row index, and a lower triangular matrix is required), phenotypic causal networks will be incorporated using structure equation models.
  * Genomic Prediction

      * Predicted values for individuals of interest can be obtained based on a user-defined prediction equation `prediction_equation`, e.g., "y1:animal + y1:age".

    For now, genomic data is always included. Genetic values including effects defined with genotype and pedigree information are returned if `prediction_equation`= false, defaulting to `false`.

      * Individual estimted genetic values and prediction error variances (PEVs) are returned if `outputEBV`=true, defaulting to `true`. Heritability and genetic

    variances are returned if `output_heritability`=`true`, defaulting to `true`. Note that estimation of heritability is computaionally intensive.
  * Miscellaneous Options

      * Print out the model information in REPL if `printout_model_info`=true; print out the monte carlo mean in REPL with `printout_frequency`, defaulting to `false`.
      * If `seed`, defaulting to `false`, is provided, a reproducible sequence of numbers will be generated for random number generation.
      * If `big_memory`=true, defaulting to `false`, a machine with  lots of memory is assumed which may speed up the analysis.
