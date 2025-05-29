```
price!(fin_obj::Option, MonteCarlo{MonteCarloModel}; kwargs...)
```

computes the option price using Monte Carlo simulation methods with the MonteCarloModel  specified. Note: Only European Options call be priced via Monte Carlo methods. 

`MonteCarloModel` types:

  * `LogDiffusion`
  * `MCBootstrap`

# Keyword arguments

## For LogDiffusion model

  * `n_sims`: Number of simulations to be run. Default 100.
  * `sim_size`: The number of generated steps in each simulated run. Default 100.

## For MCBootstrap model

  * `n_sims`: Number of simulations to be run. Defualt 100
  * `bootstrap_method`: block bootstrap method to be used. Must be a subtype of `TSBootMethod`. Defualt=`Stationary`

# Examples

```julia
prices = [1,4,3,4,2,5,6,4,7,5];
stock = Stock(prices);
call = EuroCallOption(stock, 8);

price!(call, MonteCarlo{LogDiffusion}; n_sims=50, sim_size=250)
price!(call, MonteCarlo{MCBootstrap}; bootstrap_method=CircularBlock, n_sims=10)
```
