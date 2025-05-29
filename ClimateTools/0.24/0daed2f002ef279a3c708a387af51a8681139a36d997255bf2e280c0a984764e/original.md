```
biascorrect_extremes(obs::ClimGrid, ref::ClimGrid, fut::ClimGrid; detrend=false, window::Int=15, rankn::Int=50, thresnan::Float64=0.1, keep_original::Bool=false, interp=Linear(), extrap=Flat(), gev_params::DataFrame, frac=0.25, power=1.0)
```

Combine the empirial Quantile-Quantile mapping (see [`qqmap`](@ref)) and Generalized Pareto Distribution bias-correction methods.

The tail of the distribution is corrected with a paramatric GPD, using provided parameters μ, σ and ξ contained in gevparams DataFrame. The DataFrame gevparams has column :lat, :lon, :mu, :sigma and :xi, representing the GEV parameters and the spatial location of the parameters. For each grid point, the function extracts the closest GEV parameters.

**Options specific to GPD**

**gevparams::DataFrame** represents the (external) GEV parameters to correct each grid-points.

**frac=0.25** is the fraction where the cutoff happens between QQM and GPD, as defined by **(maximum(x) - minimum(x))*frac** (e.g. For a maximum value of 150mm and a minimum value of 30mm, the linear transition will be between 30mm and 60mm).

**power=1.0** is the shape of the transition.

**Options specific to QQM**

**detrend::Bool = false (default)**. A 4th order polynomial is adjusted to the time series and the residuals are corrected.

**window::Int = 15 (default)**. The size of the window used to extract the statistical characteristics around a given julian day.

**rankn::Int = 50 (default)**. The number of bins used for the quantile estimations. The quantiles uses by default 50 bins between 0.01 and 0.99. The bahavior between the bins is controlled by the interp keyword argument. The behaviour of the quantile-quantile estimation outside the 0.01 and 0.99 range is controlled by the extrap keyword argument.

**thresnan::Float64 = 0.1 (default)**. The fraction is missing values authorized for the estimation of the quantile-quantile mapping for a given julian days. If there is more than **treshnan** missing values, the output for this given julian days returns NaNs.

**keep_original::Bool = false (default)**. If **keep_original** is set to true, the values are set to the original values in presence of too many NaNs.

**interp = Interpolations.Linear() (default)**. When the data to be corrected lies between 2 quantile bins, the value of the transfer function is linearly interpolated between the 2 closest quantile estimation. The argument is from Interpolations.jl package.

**extrap = Interpolations.Flat() (default)**. The bahavior of the quantile-quantile transfer function outside the 0.01-0.99 range. Setting it to Flat() ensures that there is no "inflation problem" with the bias correction. The argument is from Interpolation.jl package.

See also: [`qqmap`](@ref)
