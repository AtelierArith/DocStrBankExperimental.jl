```
fit(; <keyword arguments> )
```

Fit steady state or transient GM/GRSM model to RNA data for a single gene, write the result (through function finalize), and return fit results and diagnostics.

For coupled transcribing units, arguments transitions, G, R, S, insertstep, and trace become tuples of the single unit type, e.g. If two types of transcription models are desired with G=2 and G=3 then G = (2,3).

#Arguments

  * `annealsteps=0`: number of annealing steps (during annealing temperature is dropped from tempanneal to temp)
  * `burst=false`: if true then compute burst frequency
  * `cell::String=""`: cell type for halflives and allele numbers
  * `coupling=tuple()`: if nonempty, a 4-tuple where elements are 

    1. tuple of model indices corresponding to each unit, e.g. (1, 1, 2) means that unit 1 and 2 use model 1 and unit 3 uses model 2
    2. tuple of vectors indicating source units for each unit, e.g. ([2,3], [1], Int[]) means unit 1 is influenced by source units 2 and 3, unit 2 is influenced by unit 1 and unit 3 is uninfluenced.
    3. source states: tuple of vectors of strings, e.g. (["G3","R1"], []) means that model 1 influences other units whenever it is in G state 3 or R step 1 (if a number is not included (e.g. (R,0)) then all the Gstates or R steps are included),   while model 2 does not influence any other unit
    4. target transitions:tuple, e.g. ([], 4) means that model 1 is not influenced by any source while model 2 is influenced by sources at transition 4. Transitions  are number consecutively by order of the transition rates. So for a G=2 model, transition 1 is the G1 to G2 transition and transition 3 is the initiation transition
    5. Int indicating number of coupling parameters
  * `datacol=3`: column of data to use, default is 3 for rna data
  * `datatype::String=""`: String that describes data type, choices are "rna", "rnaonoff", "rnadwelltime", "trace", "tracerna", "tracejoint", "tracegrid"
  * `datacond=""`: string or vector of strings describing data, e.g. "WT", "DMSO" or ["DMSO","AUXIN"], ["gene","enhancer"]
  * `datapath=""`: path to data file or folder or array of files or folders
  * `decayrate=1.0`: decay rate of mRNA, if set to -1, value in halflives folder will be used if it exists
  * `ejectnumber=1`: number of mRNAs produced per burst, default is 1
  * `dttype=String[]`: dwelltime types, choices are "OFF", "ON", for R states and "OFFG", "ONG" for G states
  * `elongationtime=6.0`: average time for elongation, vector of times for coupled model
  * `fittedparam::Vector=Int[]`: vector of rate indices to be fit, e.g. [1,2,3,5,6,7](applies to shared rates for hierarchical models, fitted hyper parameters are specified by individual fittedparams)
  * `fixedeffects::String`: if "fixed" is included after a hyphen, then fixedeffects Tuple will be created such that R transitions are fixed to be identical
  * `fixedeffects::Tuple=tuple()`: tuple of vectors of rates that are fixed where first index is fit and others are fixed to first, e.g. ([3,8],) means index 8 is fixed to index 3 (only first parameter should be included in fittedparam) (applies to shared rates for hierarchical models)
  * `gene::String="MYC"`: gene name
  * `grid=nothing`: Int number of grid points for grid model
  * `G=2`: number of gene states, for coupled models G, R, S, and insertstep are vectors (vector for coupled models)
  * `hierarchical=tuple()`: empty tuple for nonhierarchical model; 3-tuple for hierarchical: hierarchical=(number of hyper parameter sets::Int, individual fittedparams::Vector, individual fixedeffects::Tuple),   for hierarchical models the keywords `fittedparam` and `fixedeffects` pertain to shared rates.  rates are given by a single vector that can be reshaped into a matrix where the columns correspond to the model rates and noise params, the first nhyper rows pertain to the shared and hyper parameter rates (whether fit or not),    usually the first row is the shared and mean hyper parameters and the 2nd are the standard deviations, the rest of the rows are the individual rates and noise params
  * `infolder::String=""`: result folder used for initial parameters
  * `inlabel::String=""`: label of files used for initial conditions
  * `insertstep=1`: R step where reporter is inserted
  * `label::String=""`: label of output files produced
  * `maxtime=60`: maximum wall time for run, default = 60 min
  * `method=Tsit5()`: DifferentialEquations.jl numerical method (e.g. Tsit5(), Tsit5(),...); use a tuple for hierarchical models: method = tuple(method, Bool) = (numerical method (currently not used), true if transition rates are shared)
  * `nalleles=1`: number of alleles, value in alleles folder will be used if it exists, for coupled models, nalleles is only used when computing steady state RNA histograms and considered uncoupled.  For add coupled alleles as units and set nalleles to 1.
  * `nchains::Int=2`: number of MCMC chains = number of processors called by Julia, default = 2
  * `noisepriors=[]`: priors of observation noise (use empty set if not fitting traces), superseded if priormean is set
  * `onstates=Int[]`: vector of on or sojourn states, e.g. [2], if multiple onstates are desired, use vector of vectors, e.g. [[2,3],Int[]], use empty vector for R states or vector of empty vectors for R states in coupled models, do not use Int[] for R=0 models
  * `optimize=false`: use optimizer to compute maximum likelihood value
  * `priormean=Float64[]`: mean rates of prior distribution (must set priors for all rates including those that are not fitted)
  * `priorcv=10.`: (vector or number) coefficient of variation(s) for the rate prior distributions, default is 10.
  * `probfn=prob_Gaussian`: probability function for HMM observation probability (i.e., noise distribution)
  * `propcv=0.01`: coefficient of variation (mean/std) of proposal distribution, if cv <= 0. then cv from previous run will be used
  * `resultfolder::String=test`: folder for results of MCMC run
  * `R=0`: number of pre-RNA steps (set to 0 for classic telegraph models)
  * `root="."`: name of root directory for project, e.g. "scRNA"
  * `samplesteps::Int=1000000`: number of MCMC sampling steps
  * `S=0`: number of splice sites (set to 0 for classic telegraph models and R - insertstep + 1 for GRS models)
  * `splicetype=""`: RNA pathway for GRS models, (e.g., "offeject" = spliced intron is not viable)
  * `temp=1.0`: MCMC temperature
  * `tempanneal=100.`: annealing temperature
  * `temprna=1.`: reduce RNA counts by temprna compared to dwell times
  * `traceinfo=(1.0, 1., -1, 1., 0.5)`: 5 tuple = (frame interval of intensity traces in minutes, starting frame time in minutes, ending frame time (use -1 for last index), fraction of observed active traces, background mean)   for simultaneous joint traces, the fraction of active traces is a vector of the active fractions for each trace, e.g. (1.0, 1., -1, [.5, .7], [0.5,0.5])    If active fraction is 1.0, then traceinfo can be a 3-tuple, e.g. (1.0, 1., -1) since background correction is not needed   Note that all traces are scaled by the maximum of the medians of all the traces, the traces are all scaled by the same factor since the signal amplitude should be the same
  * `TransitionType=""`: String describing G transition type, e.g. "3state", "KP" (kinetic proofreading), "cyclic", or if hierarchical, coupled
  * `transitions::Tuple=([1,2],[2,1])`: tuple of vectors that specify state transitions for G states, e.g. ([1,2],[2,1]) for classic 2-state telegraph model and ([1,2],[2,1],[2,3],[3,1]) for 3-state kinetic proofreading model, empty for G=1
  * `warmupsteps=0`: number of MCMC warmup steps to find proposal distribution covariance
  * `writesamples=false`: write out MH samples if true, default is false
  * `zeromedian=false`: if true, subtract the median of each trace from each trace, then scale by the maximum of the medians

# Returns

  * `fits`: MCMC fit results (posterior samples, log-likelihoods, etc.)
  * `stats`: Summary statistics for parameters
  * `measures`: Diagnostic measures (including WAIC and its standard error, which is now for the total WAIC and scaled by sqrt(n_obs))
  * `data`, `model`, `options`: The data, model, and options structures used

# Notes

  * If `propcv < 0`, proposal covariance is read from previous run if available.
  * WAIC standard error is for the total WAIC (not per observation), and is scaled by sqrt(n_obs).
  * File and folder conventions may have changed; see README for details.

# Example

If you are in the folder where data/HCT116_testdata is installed, you can fit the mock RNA histogram running 4 MCMC chains with:

```julia
julia> fits, stats, measures, data, model, options = fit(nchains = 4)
```
