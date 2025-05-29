```
Mk, Mk_adc = get_Mk(seq::Sequence, k; Δt=1, skip_rf=zeros(Bool, sum(is_RF_on.(seq))))
```

Computes the $k$th-order moment of the Sequence `seq` given by the formula $\int_0^T t^k G(t) dt$.

# Arguments

  * `seq`: (`::Sequence`) Sequence struct
  * `k`: (`::Integer`) order of the moment to be computed
  * `Δt`: (`::Real`, `=1`, `[s]`) nominal delta time separation between two time samples   for ADC acquisition and Gradients
  * `skip_rf`: (`::Vector{Bool}`, `=zeros(Bool, sum(is_RF_on.(seq)))`) boolean vector which   indicates whether to skip the computation for resetting the integral for excitation or   refocusing RF type

# Returns

  * `Mk`: (`3-column ::Matrix{Real}`) $k$th-order moment
  * `Mk_adc`: (`3-column ::Matrix{Real}`) $k$th-order moment sampled at ADC times
