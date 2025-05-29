```
simulator(r, transitions, G, R, S, insertstep; coupling=tuple(), nalleles=1, nhist=20, onstates=Int[], bins=Float64[], traceinterval::Float64=0.0, probfn=prob_Gaussian, noiseparams=4, totalsteps::Int=10000, totaltime::Float64=0.0, tol::Float64=1e-6, reporterfn=sum, splicetype="", verbose::Bool=false)
```

Simulate any GRSM model. Returns steady state mRNA histogram. If bins not a null vector will return a vector of the mRNA histogram and ON and OFF time histograms. If traceinterval > 0, it will return a vector containing the mRNA histogram and the traces

#Arguments

  * `r`: vector of rates
  * `transitions`: tuple of vectors that specify state transitions for G states, e.g. ([1,2],[2,1]) for classic 2 state telegraph model and ([1,2],[2,1],[2,3],[3,1]) for 3 state kinetic proof reading model
  * `G`: number of gene states
  * `R`: number of pre-RNA steps (set to 0 for classic telegraph models)
  * `S`: number of splice sites (set to 0 for G (classic telegraph) and GR models and R for GRS models)
  * `insertstep`: reporter insertion step

#Named arguments

  * `bins::Vector=Float64[]`: vector of time bin vectors for each set of ON and OFF histograms or vector of vectors of time bins (one time bin vector for each onstate)
  * `coupling=tuple()`: if nonempty, a 4-tuple where elements are

    1. tuple of model indices corresponding to each unit, e.g. (1, 1, 2) means that unit 1 and 2 use model 1 and unit 3 uses model 2
    2. tuple of vectors indicating source units for each unit, e.g. ([2,3], [1], Int[]) means unit 1 is influenced by source units 2 and 3, unit 2 is influenced by unit 1 and unit 3 is uninfluenced.
    3. source states, e.g. (3,0) means that model 1 influences other units whenever it is in G state 3, while model 2 does not influence any other unit
    4. target transitions, e.g. (0, 4) means that model 1 is not influenced by any source while model 2 is influenced by sources at G transition 4.
    5. Int indicating number of coupling parameters
  * `nalleles`: Number of alleles
  * `nhist::Int`: Size of mRNA histogram
  * `onstates::Vector`: a vector of vector of ON states (use empty set for any R step is ON), ON and OFF time distributions are computed for each ON state set
  * `probfn`=prob_Gaussian: reporter distribution
  * `reporterfn`=sum: how individual reporters are combined
  * `splicetype`::String: splice action
  * `tol`::Float64=1e-6: convergence error tolerance for mRNA histogram (not used when simulating traces are made)
  * `totalsteps`::Int=10000000: maximum number of simulation steps (not usred when simulating traces)
  * `totaltime`::Float64=0.0: total time of simulation
  * `traceinterval`: Interval in minutes between frames for intensity traces.  If 0, traces are not made.
  * `verbose::Bool=false`: flag for printing state information

#Example:

julia> h=simulator([.1, .1, .1, .1, .1, .1, .1, .1, .1, .01],([1,2],[2,1],[2,3],[3,2]),3,2,2,1,nhist=20,bins=[collect(2.:2.:200),collect(.2:.2:20)],onstates=[Int[],[3]],nalleles=2, totalsteps = 200000) 5-element Vector{Vector}:  [7823.967526508377, 33289.19787176562, 69902.6774554014, 92942.59127561412, 91816.91189325438, 70259.88319069796, 43895.28637479579, 22426.725922619895, 9005.190755732247, 3043.2417332890695, 1005.6412773072143, 203.11430396725336, 6.420639815427421, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0]  [2911, 2568, 2228, 1694, 1354, 1088, 819, 661, 514, 401  …  0, 0, 0, 0, 0, 0, 0, 0, 0, 0]  [622, 643, 592, 596, 553, 524, 520, 489, 448, 437  …  19, 13, 12, 12, 14, 10, 10, 17, 8, 8]  [550, 584, 569, 555, 498, 510, 497, 495, 489, 487  …  89, 96, 107, 99, 89, 103, 86, 97, 87, 77]  [593, 519, 560, 512, 492, 475, 453, 468, 383, 429  …  84, 73, 85, 92, 73, 81, 85, 101, 79, 78]
