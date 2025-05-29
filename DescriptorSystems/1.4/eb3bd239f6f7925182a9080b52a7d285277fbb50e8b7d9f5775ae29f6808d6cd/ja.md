```
 opnorm(sys[, p = Inf]; kwargs...) 
 opnorm(sys, 2; kwargs...) -> sysnorm
 opnorm(sys, Inf; kwargs...) -> (sysnorm, fpeak)
 opnorm(sys; kwargs...) -> (sysnorm, fpeak)
```

記述子システム `sys = (A-λE,B,C,D)` に対して、伝達関数行列 `G(λ)` の `L2` または `L∞` システムノルム `sysnorm` をベクトル `p`-ノルムによって計算します。ここで有効な値の `p` は `2` または `Inf` です。`L∞` ノルムの場合、周波数 `fpeak` も返され、ここで `G(λ)` はそのピークゲインを達成します。許可されるキーワード引数の説明については、[`gh2norm`](@ref) と [`ghinfnorm`](@ref) を参照してください。  
