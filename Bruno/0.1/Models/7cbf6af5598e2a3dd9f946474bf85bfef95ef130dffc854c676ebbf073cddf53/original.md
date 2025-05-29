```
price!(fin_obj<:CallOption, pricing_model::Type{<:Model};kwargs...)
```

Computes the value of a given financial object. 

# Syntax

```
price!(fin_obj, PricingModelType; kwargs...)
```

key word arguments vary depending on the Pricing Model Type.

# Example

```julia
# create a base asset
a_stock = Stock(41; volatility=.3)

# create a European call option 
a_fin_inst = EuroCallOption(a_stock, 40; risk_free_rate=.05) 

# add binomial tree call value to the options value dictionary
price!(a_fin_inst, BinomialTree)  
```
