```
blocking_analysis_data(v::AbstractVector; kwargs...) ->
(; br::BlockingResult, df::DataFrame)
```

Perform a [`blocking_analysis`](@ref) and return the summary result `br` as well as a `DataFrame` `df` with information about the standard error in each blocking step.

For a description of the keyword arguments see [`blocking_analysis`](@ref).

## Example

```julia-repl
julia> data = smoothen(rand(10_000), 2^6); # generate correlated data

julia> br, df = blocking_analysis_data(data)
(br = BlockingResult{Float64}
  mean = 0.5088 ± 0.0029
  with uncertainty of ± 0.00023454488294744232
  from 78 blocks after 7 transformations (k = 8).
, df = 13×6 DataFrame
 Row │ blocks  mean      std_err      std_err_err  p_cov       mj
     │ Int64   Float64   Float64      Float64      Float64     Float64
─────┼──────────────────────────────────────────────────────────────────────
   1 │  10000  0.508806  0.000375044  2.6521e-6    1.40658e-7  9715.08
   2 │   5000  0.508806  0.000528547  5.28599e-6   2.79361e-7  4778.14
   3 │   2500  0.508806  0.000743386  1.05152e-5   5.52622e-7  2298.64
   4 │   1250  0.508806  0.00104064   2.08212e-5   1.08293e-6  1056.24
   5 │    625  0.508806  0.00144177   4.08121e-5   2.07871e-6   427.949
   6 │    312  0.508736  0.00194209   7.78707e-5   3.77171e-6   128.711
   7 │    156  0.508736  0.00247921   0.00014081   6.14647e-6    17.3075
   8 │     78  0.508736  0.00291063   0.000234545  8.47174e-6     0.731386
   9 │     39  0.508736  0.00284613   0.000326474  8.10046e-6     0.901054
  10 │     19  0.508241  0.0026998    0.000449967  7.28892e-6     2.85915
  11 │      9  0.507939  0.00359907   0.000899766  1.29533e-5     1.08644
  12 │      4  0.509327  0.00440559   0.00179857   1.94092e-5     0.0370381
  13 │      2  0.509327  0.00432708   0.00305971   1.87237e-5     0.125)

julia> using StatsPlots; unicodeplots();

julia> plot([br.k,br.k],[0.0,maximum(df.std_err.+df.std_err_err)], label="m test");

julia> @df df plot!(
           1:length(:std_err), :std_err;
           err=:std_err_err, xlabel="k", label="std err",
           title="std err vs blocking steps"
       )
               ⠀⠀⠀⠀⠀⠀⠀⠀⠀std err vs blocking steps⠀⠀⠀⠀⠀⠀⠀⠀
               ┌────────────────────────────────────────┐
    0.00423501 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠀⠀⠀⠀│ m test
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠀⠀⢸⠀⠀⠀⠀│ std err
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⢸⠀⠀⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀⢸⠀⠀⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⡠⢺⠒⠒⢺⠀⠀⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⡀⠀⠀⡆⣀⠤⡗⠉⠀⢸⠀⠀⢸⡆⠀⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⡧⠤⠔⡗⠊⠉⡏⠀⠀⡇⠀⠀⢸⠀⠀⢸⢣⠀⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠔⠁⡇⠀⠀⠁⠀⠀⠁⠀⠀⠁⠀⠀⠀⠀⠀⢸⠸⡀⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠴⠁⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⠀⡇⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠔⠁⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠔⠊⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⣦⠀│
               │⠀⠀⠀⠀⠀⠀⠀⠀⡠⠔⠒⠁⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢹⠀│
               │⠀⠀⠀⢀⣀⠤⠒⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀│
               │⠀⠒⠉⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⠀│
   -0.00012335 │⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠧⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤│
               └────────────────────────────────────────┘
               ⠀0.64⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀k⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀13.36⠀
```

A vertical line at `k==8` indicates the blocking step identified by hypothesis testing to decorrelate the time series data. The decorrelation length can thus be estimated at $2^{k-1} = 2^7 = 128$. Note that the data was correlated with a sliding window of $2^6$ steps.

See [`blocking_analysis`](@ref), [`BlockingResult`](@ref).
