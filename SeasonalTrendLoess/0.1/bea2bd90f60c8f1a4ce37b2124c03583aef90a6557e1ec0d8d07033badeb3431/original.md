```
stl(Yv, np; robust=false, 
            nl=nextodd(np), 
            ns=10*length(Yv)+1,
            nt=nextodd(1.5*np/(1-1.5/ns)), 
            ni=robust ? 1 : 2,
            no=0,
            spm=false,
            qsmp=max(div(np,7),2))
```

Decompose a time series into trend, seasonal, and remainder components. "STL has a simple design that consists of a sequence of applications of the loess smoother; the simplicity  allows analysis of the properties of the procedure and allows fast computation, even for very long time series and large amounts of trend and seasonal smoothing. Other features of STL  are specification of amounts of seasonal  and trend smoothing that range, in a nearly continous way, from very small amount of smoothing to a very large  amount; robust estimates of the trend and seasonal components that are not distorted by aberrant behavior in the data; specification of the period of the seasonal component to any intenger multiple of the time sampling interval greater than one; and the ability to decompose time series with missing values."*

All default values are chosen following the recommendations of the original paper when those were recommended.  `ns` is recommended to be chosen of the basis of knowledge of the time series and on the basis of diagnostic methods; it must nonethelessbe always odd and at least 7. A default value is not advised on the original  paper, instead the same default value used in the stl implementation in R in usere here. for `no` the authors advise 5 ("safe value") or 10 ("near certainty of convergence") cycles or a  convergence criterion when robustness is required, in this case when `robust` is true computations  stop when convergence is achieved in trend and seasonality. for `qsmp` the authors do not adivise a default but they use a value close to div(`np`,7).

# Arguments

  * `np`: Seasonality.
  * `robust`: Robust stl.
  * `nl`: Smoothing parameter of the low-pass filter.
  * `ns`: Smoothing parameter for the seasonal component.
  * `nt`: Smoothing parameter for the trend decomposition.
  * `ni`: Number of inner loop cycles.
  * `no`: Number of outer loop cycles.
  * `spm`: Seasonal post-smoothing.
  * `qsmp`: Loess q window for Seasonal post-smoothing.
  * `verbose`: If true shows updates for the Seasonal and Trend convergence.
  * `cth`: Corvengence threshold for Seasonal and Trend.

# Returns

An `STL` object with the seasonal, trend and remainder components.

  * STL: A Seasonal, Trend Decomposition Procedure Based on Loess" Robert B. Cleveland, William S. Cleveland, Jean E. McRae, and Irma Terpenning. Journal of Official Statistics Vol. 6. No. 1, 1990, pp. 3-73 (c) Statistics Sweden.

# Examples

```julia-repl
julia> stl_co2 = stl(co2(),365; robust=true, spm=true)
[ Info: Dataset used in Cleveland et al. paper
[ Info: Corvengence achieved (< 0.01); Stopping computation...
STL{TimeSeries.TimeArray{Union{Missing, Float64},2,
Dates.Date,Array{Union{Missing, Float64},2}}}
(4609×3 TimeSeries.TimeArray{Union{Missing, Float64},2,
Dates.Date,Array{Union{Missing, Float64},2}} 1974-05-17 to 1986-12-31, 
"stl(Yn, np=365; nl=365, ns=46091, nt=549, ni=1, no=0, spm=true, qsmp=52)")
julia> plot(stl_co2)
```
