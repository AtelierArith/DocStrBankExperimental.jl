```
epgRelaxation( R1::AbstractFloat, R2::AbstractFloat, t::AbstractFloat, F::Vector{T}, Z::Vector{T}) where T
```

applies relaxation matrices to a set of EPG states.

# Arguments

  * `R1::AbstractFloat`   - R1
  * `R2::AbstractFloat`   - R2
  * `t::AbstractFloat`    - length of time interval in s
  * `F::Vector{T}`  - transverse dephasing stats
  * `Z::Vector{T}`  - longitudinal dephasing stats
