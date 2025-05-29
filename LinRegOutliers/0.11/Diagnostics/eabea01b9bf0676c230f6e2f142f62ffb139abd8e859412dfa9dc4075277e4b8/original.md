```
hadimeasure(setting; c = 2.0)
```

Apply Hadi's regression diagnostic for a given regression setting

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `c::Float64`: Critical value selected between 2.0 - 3.0. The default is 2.0.

# Example

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> hadimeasure(setting)
```

# References

Chatterjee, Samprit and Hadi, Ali. Regression Analysis by Example. 	 5th ed. N.p.: John Wiley & Sons, 2012.
