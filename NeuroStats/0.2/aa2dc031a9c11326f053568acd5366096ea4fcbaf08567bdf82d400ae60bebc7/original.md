```
stdp(s1, s2, n1, n2; <keyword arguments>)
```

Calculate pooled standard deviation when number of subjects in groups are different.

# Arguments

  * `s1::Real`
  * `s2::Real`
  * `n1::Int64`
  * `n2::Int64`
  * `type::Symbol=:cohen`: use Cohen's equation (`:cohen`) or maximum likelihood estimator by Hedges and Olkin (`:hedges`)

# Returns

  * `ps::Float64`
