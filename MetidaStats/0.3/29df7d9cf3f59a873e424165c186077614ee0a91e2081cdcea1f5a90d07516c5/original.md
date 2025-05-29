```
descriptives(data, vars, sort = nothing; kwargs...)
```

  * kwargs:
  * `skipmissing` - drop NaN and Missing values, default = true;
  * `skipnonpositive` - drop non-positive values (and NaN, Missing) for "log-statistics" - :geom, :geomean, :logmean, :logvar, :geocv;
  * `stats` - default set `stats = [:n, :mean, :sd, :se, :median, :min, :max]`;
  * `corrected` - use corrected var (true);
  * `level` - level for confidence intervals (0.95);

Possible values for `stats` is: 

  * :n - number of observbations;
  * :posn - positive (non-negative) number of observations;
  * :mean - arithmetic mean;
  * :var - variance;
  * :bvar - variance with no correction;
  * :geom - geometric mean;
  * :logmean - arithmetic mean for log-transformed data;
  * :logvar - variance for log-transformed data $σ^2_{log}$;
  * :sd - standard deviation (or σ);
  * :se - standard error;
  * :cv - coefficient of variation;
  * :geocv - coefficient of variation for log-transformed data ($CV = sqrt{exp(σ^2_{log})-1}$);
  * :lci - lower confidence interval;
  * :uci - upper confidence interval;
  * :lmeanci - lower confidence interval for mean;
  * :umeanci - lower confidence interval for mean;
  * :median - median,;
  * :min - minimum;
  * :max - maximum;
  * :range - range;
  * :q1 - lower quartile;
  * :q3 - upper quartile;
  * :iqr - inter quartile range;
  * :kurt - kurtosis;
  * :skew - skewness;
  * :harmmean - harmonic mean;
  * :ses standard error of skewness;
  * :sek - standard error of kurtosis;
  * :sum - sum.
