```
stdp(x1, x2; <keyword arguments>)
```

Calculate pooled standard deviation.

# Arguments

  * `x1::AbstractVector`
  * `x2::AbstractVector`
  * `type::Symbol=:cohen`: use Cohen's equation (`:cohen`) or maximum likelihood estimator by Hedges and Olkin (`:hedges`)

# Returns

  * `ps::Float64`
