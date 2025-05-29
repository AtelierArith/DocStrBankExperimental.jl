```
project_k!(x::AbstractVector, k::Integer)
```

`x`の最大の`k`エントリ以外をすべて0に設定します。

# 例:

```julia-repl
using MendelIHT
x = [1.0; 2.0; 3.0]
project_k!(x, 2) # 最大の2つのエントリを保持
julia> x
3-element Array{Float64,1}:
 0.0
 2.0
 3.0
```

# 引数:

  * `x`: 投影するベクトル。
  * `k`: `x`の保持するコンポーネントの数。
