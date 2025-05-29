```julia
CheckGaugeValidity(lat::Lattice{T}, A::Function ; _kwargs::Dict = Dict(), accuracy::Int64 = 5) --> Bool 
```

格子 `lat` に対して周期境界条件の下でゲージベクトルポテンシャル `A` が有効かどうかをチェックします。
