draw!(s::RWMState, L::Cholesky, sc::AbstractFloat)

Draw proposal from `s.x` to `s.y` using scaling `sc*L.L`, with default `sc=1.0`.
