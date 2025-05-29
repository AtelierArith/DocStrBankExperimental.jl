```
item_characteristic_curve(model, item, response)
item_characteristic_curve(model, item)
```

Create a plot of the item characteristic curve for `response` of `item`.

An item characteristic curve plots the probability for `response` of `item` given the person ability θ.

If `response` is omitted, the default plot behaviour depends on `model`:

  * For models where `response_type(model) == Dichotomous` the item characteristic curve for response = 1 is plotted, i.e. the probability of a correct response.
  * For models where `response_type(model) <: Union{Nominal, Ordinal}` all category characteristic curves are plotted.

# Plot attributes

## Generic

  * `color`: The color of the item characteristic curve.
  * `uncertainty_color`: The color of the displayed uncertainty information. For plots with uncertainty intervals this is the color of the confidence band. For plots with sample based uncertainty information this is the line color of the samples.
  * `theta`: The values of `theta` for which to plot the item characteristic curve. default: -3.0:0.01:3.0.
  * `show_data`: Overlay observed data in the plot. Ability estimates are aggregated according to `bins`. For models with `estimation_type(model) == SamplingEstimate` the posterior means of ability estimates are used for binning. default: false.
  * `bins`: The number of bins for the observed data. default: 6.

## Specific

### Models with `SamplingEstimate`

  * `samples`: The number of samples to plot. default: `1000`
  * `uncertainty_type`: Changes how the uncertainty of the estimate is displayed. If `uncertainty_type = :samples`, then iterations from the MCMC estimation are plotted. If `unvertainty_type = :interval`, then uncertainty intervals are plotted. default: `:samples`
  * `quantiles`: The lower and upper quantile for uncertainty intervals. default: `(0.1, 0.9)`
  * `aggregate_fun`: A function that aggregates MCMC samples. The provided function must take a vector as input and output a scalar value. If `aggregate_fun = nothing` no aggregate is plotted. default: mean
