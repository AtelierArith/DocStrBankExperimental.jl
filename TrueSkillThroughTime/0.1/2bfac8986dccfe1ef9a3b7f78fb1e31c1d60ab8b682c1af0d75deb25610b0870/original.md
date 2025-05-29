The `Game` class

```
Game(teams::Vector{Vector{Player}}, result::Vector{Float64}, p_draw::Float64, weights::Vector{Vector{Float64}})
```

Properties:

  * `teams::Vector{Vector{Player}}`
  * `result::Vector{Float64}`
  * `p_draw::Float64`
  * `weights::Vector{Vector{Float64}}`
  * `likelihoods::Vector{Vector{Gaussian}}`
  * `evidence::Float64`
