```
BLAKJac_optimize(trajectorySet, options::Dict, mersenneTwisterSeed=1)
```

Optimization procedure according to BLAKJac

For a given ky pattern (or (ky,kz)-pattern) and given some options, it generates a sequence of RF pulses pretending to be optimized. The seed parameter can be provided as an integer, to allow different realizations of random-value initializations. (By default, it should reproducably generate the same sequence on every call)

A meaningful set of options can be pre-defined by "options = Dict(); BLAKJac.BLAKJac_defaults!(trajectorySet, options)"

To understand some option parameters, one must know that the optimization consists of two stages (of which often only one is used); the first stage optimizes cubic-spline-interpolated smooth RF-patterns, with ever increasing number of degrees of freedom ("increasing resolution"). In the second stage, successive portions of the sequence are "fine-tuned" by optimizing the sequence portion by portion, taking all of the optimized  "past" for granted

Option parameters are:

  * `nky`             Extent of ky
  * `sizeSteps`       Array of integers; provides subsequent "resolutions" in the first stage
  * `portion_size`    The size of a portion to be optimized
  * `portion_step`    after one portion is considered sufficiently optimized, the "next" portion is addressed, which is `portion_step` further on.                   Preferably, `portion_step` is smaller than `portion_size`.
  * `opt_iterations_limit`  Int. Controls the total of first-stage and second-stage steps. To switch off the second stage, it has to be length of sizeSteps.                     Setting it to an arbitrary high value means "full processing"
  * `opt_complex`     Bool. Allow all pulses to have a phase. Deprecated.
  * `opt_slow_phase`  Bool. A very controlled way to optimize the phase: what is optimized is a low-resolution of the second derivative of the phase
  * `opt_imposed_2nd_derivative_of_phase`        (Vector over nTR elements) To be filled in if the 2nd derivative of phase is not to be optimized -                                            i.e. if it is pre-defined
  * `opt_initialize`  Controls how the RF-pattern is optimized before entering optimization. Can be one of `"ones"` (all angles are 1 degree),                      `"ernst"` (all angles are set to the Ernst angle given a reference T1 and the TR), `"init_angle"` (all set to `opt_init_angle`),                     `"cRandom30"` (put it to random values with a deviation of 30 degrees) or `"RF_shape"` (initial shape provided by option                      `"rfFunction"`)
  * `rfFunction`      (see above)
  * `opt_init_angle`  (see above)
  * `opt_focus`       Which property should the optimizer focus on? Can be any of `"rho"`, `"T1"`, `"T2"`, `"mean"`, `"max"` or `"weighted"`;                      the last one                    combines the *relative* noise levels of T1 and T2 (relative to T1ref resp. T2ref)
  * `opt_criterion`   Can be any of `"noise_level"`, `"low-flip corrected noise"`, `"sar-limited noise"`, `"information content"`,                  `"information content penalized"`,                    `"B1 sensitivity sar-limited"`, `"B1 sensitivity/noise mix, sar-limited"`
  * `lambda_B1`       A regularization parameter for the B1 sensitivity
  * `lambda_CSF`      A regularization parameter for the CSF sensitivity
  * `opt_keep_positive`   Bool. If true, negative angles are heavily penalized
  * `opt_emergeCriterion` Int. Calls for intermediate displays of the RF shape every opt_emergeCriterion iterations
  * `opt_method`      optimizer function, e.g. NelderMead
  * `optpars`         optimization parameters - see Optim package.
