```
duration(keyrate::KeyRateDuration,curve,cashflows)    
duration(keyrate::KeyRateDuration,curve,cashflows,timepoints)
duration(keyrate::KeyRateDuration,curve,cashflows,timepoints,krd_points)
```

Calculate the key rate duration by shifting the **zero** (not par) curve by the kwarg `shift` at the timepoint specified by a KeyRateDuration(time).

The approach is to carve up the curve into `krd_points` (default is the unit steps between `1` and  the last timepoint of the casfhlows). The  zero rate corresponding to the timepoint within the `KeyRateDuration` is shifted by `shift` (specified by the `KeyRateZero` or `KeyRatePar` constructors. A new curve is created from the shifted rates. This means that the  "width" of the shifted section is ± 1 time period, unless specific points are specified via `krd_points`.

The `curve` may be any FinanceModels.jl curve (e.g. does not have to be a curve constructed via `FinanceModels.Zero(...)`).

!!! Experimental: Due to the paucity of examples in the literature, this feature does not have unit tests like the rest of JuliaActuary functionality. Additionally, the API may change in a future major/minor version update.

# Examples

```julia-repl
julia> riskfree_maturities = [0.5, 1.0, 1.5, 2.0];

julia> riskfree    = [0.05, 0.058, 0.064,0.068];

julia> rf_curve = FinanceModels.Zero(riskfree,riskfree_maturities);

julia> cfs = [10,10,10,10,10];

julia> duration(KeyRate(1),rf_curve,cfs)
8.932800152336995

```

# Extended Help

Key Rate Duration is not a well specified topic in the literature and in practice. The reference below suggest that shocking the par curve is more common  in practice, but that the zero curve produces more consistent results. Future versions may support shifting the par curve.

References: 

  * [Quant Finance Stack Exchange: To compute key rate duration, shall I use par curve or zero curve?](https://quant.stackexchange.com/questions/33891/to-compute-key-rate-duration-shall-i-use-par-curve-or-zero-curve)
  * (Financial Exam Help 123](http://www.financialexamhelp123.com/key-rate-duration/)
