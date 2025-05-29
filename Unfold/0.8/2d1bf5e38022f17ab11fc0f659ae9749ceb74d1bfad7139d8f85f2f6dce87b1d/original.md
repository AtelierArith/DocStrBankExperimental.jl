```
fit(type::UnfoldModel,d::Vector{Pair},tbl::AbstractDataFrame,data::Array)
fit(type::UnfoldModel,f::FormulaTerm,tbl::AbstractDataFrame,data::Array{T,3},times)
fit(type::UnfoldModel,f::FormulaTerm,tbl::AbstractDataFrame,data::Array{T,2},basisfunction::BasisFunction)
```

Generates Designmatrix & fits model, either mass-univariate (one model per epoched-timepoint) or time-expanded (modeling linear overlap).

## keyword arguments

  * `fit::Bool` (default: `true`) - fit the model after constructing the designmatrix. Setting this to `false` is sometimes helpful if you only want to inspect the designmatrix.
  * `contrasts::Dict`: (default: `Dict()`) contrast to be applied to formula. Example: `Dict(:my_condition=>EffectsCoding())`. More information here: https://juliastats.org/StatsModels.jl/stable/contrasts/
  * `eventcolumn::Union{Symbol,String}` (default `:event`) - the column in `tbl` to differentiate the basisfunctions as defined in `d::Vector{Pair}`
  * `solver::function`: (default: `solver_default`). The solver used for `y=Xb`, e.g. `(X,y;kwargs...) -> solver_default(X,y;kwargs...)`. There are faster & alternative solvers available, see `solver_predefined` for a list of options, see `solver benchmark` in the online documentation. To use the GPU, you can provide the data as a `CuArray` after `using CUDA`. Please change the solver to e.g. `solver_predef(X,y;solver=:qr)` as lsmr+cuda => crash typically. It's worth though, speed increases >100x possible
  * `show_progress::Bool` (default `true`) - show progress via ProgressMeter - passed to `solver`
  * `eventfields::Array: (optional, default`[:latency]`) Array of symbols, representing column names in`tbl`, which are passed to basisfunction event-wise. First field of array always defines eventonset in samples.

If a `Vector[Pairs]` is provided, it has to have one of the following structures: For **deconvolution** analyses (use `Any=>(f,bf)` to match all rows of `tbl` in one basis functions). Assumes `data` is a continuous EEG stream, either a `Vector` or a `ch x time` `Matrix`

```julia
f1 = @formula(0~1+my_condition)
[
 :A=>(f1,firbasis((-0.1,1),128), # sfreq = 128Hz
 :B=>(f2,firbasis((-3,2),128)
]
```

for **mass-univariate** analyses without deconvolution. Assumes `data` to be cut into epochs already (see `Unfold.epoch`). Follows *eeglab* standard `ch x time x trials`:

```julia
timesvector = range(-0.1,3,step=1/100)
[
 :A=>(f1,timesvector),
 :B=>(f2,timesvector)
]
```

## Notes

  * The `type` can be specified directly as well e.g. `fit(type::UnfoldLinearModel)` instead of relying on the automatic inference
  * The data is reshaped if it is missing one dimension to have the first dimension then `1` "Channel".

## Examples

Mass Univariate Linear

```julia-repl
julia> data,evts = UnfoldSim.predef_eeg()
julia> data_e,times = Unfold.epoch(data=data,tbl=evts,τ=(-1.,1.9),sfreq=100) # cut the data into epochs. data_e is now ch x times x epoch

julia> f  = @formula 0~1+continuousA+continuousB
julia> model = fit(UnfoldModel,f,evts,data_e,times)
# or:
julia> model = fit(UnfoldModel,[Any=>(f,times)],evts,data_e)
```

Timexpanded Univariate Linear

```julia-repl
julia> basisfunction = firbasis(τ=(-1,1),sfreq=10)
julia> model = fit(UnfoldModel,f,evts,data,basisfunction)
# or
julia> model = fit(UnfoldModel,[Any=>(f,basisfunction],evts,data)
```
