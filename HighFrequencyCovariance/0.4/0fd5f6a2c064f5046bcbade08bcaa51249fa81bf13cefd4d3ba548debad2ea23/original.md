```
generate_random_path(
   dimensions::Integer,
   ticks::Integer;
   syncronous::Bool = false,
   rng::Union{MersenneTwister,StableRNG} = MersenneTwister(1),
   vol_dist::Distribution = Uniform(
       0.1 / sqrt(252 * 8 * 3600),
       0.5 / sqrt(252 * 8 * 3600),
   ),
   refresh_rate_dist::Distribution = Uniform(0.5, 5.0),
   time_period_per_unit::Dates.Period = Second(1),
   micro_noise_dist::Distribution = Uniform(
       vol_dist.a * sqrt(time_period_ratio(Minute(5), time_period_per_unit)),
       vol_dist.b * sqrt(time_period_ratio(Minute(5), time_period_per_unit)),
   ),
   assets::Union{Vector,Missing} = missing,
   brownian_corr_matrix::Union{Hermitian,Missing} = missing,
   vols::Union{Vector,Missing} = missing,
   rng_timing::Union{MersenneTwister,StableRNG} = MersenneTwister(1),
)
```

Generate a random path of price updates with a specified number of dimensions and ticks. There are options for whether the data is syncronous or asyncronous, the volatility of the price processes, the refresh rate on the (exponential) arrival times of price updates, the minimum and the maximum microstructure noises.

Note the defaults are chosen to reflect a highcap stock with annualised volatility between 10% and 50%. The standard deviation of microstructure noise is of the same order of magnitude as 5 minutes standard deviation of return. `vol * sqrt(60*5)` if vol is in seconds. Refreshed ticks every 0.5-5 seconds (in expectation).

### Inputs

  * `dimensions` - The number of assets.
  * `ticks` - The number of ticks to produce.
  * `syncronous` - Should ticks be syncronous (for each asset) or asyncronous.
  * `rng` - The Random.MersenneTwister or StableRNGs.Stable used for RNG.
  * `vol_dist` - The distribution to draw volatilities from (only used if vols is missing).
  * `refresh_rate_dist` - The distribution to draw refresh rates (exponential distribution rates) from.
  * `time_period_per_unit` - What time period should the time column correspond to.
  * `micro_noise_dist`  - The distribution to draw assetwise microstructure noise standard deviations are drawn from.
  * `assets` - The names of the assets that you want to use. The length of this must be equal to the `dimensions` input.
  * `brownian_corr_matrix` - The correlation matrix to use. This is sampled from the Inverse Wishart distribution if none is input.
  * `vols` - The volatilities to use. These are sampled  from the uniform distribution between `min_noise_var` and `max_noise_var`.

### Returns

  * A `SortedDataFrame` of tick data.
  * A `CovarianceMatrix` representing the true data generation process used in making the tick data.
  * A `Dict` of microstructure noise variances for each asset.
  * A `Dict` of update rates for each asset.
