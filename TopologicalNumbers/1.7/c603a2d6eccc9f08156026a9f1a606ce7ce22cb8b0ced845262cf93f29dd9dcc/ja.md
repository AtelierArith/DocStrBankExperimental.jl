```
findWeylPoint(Hamiltonian::Function; N::Int=10, gapless::T=[1e-1, 1e-2, 1e-3, 1e-4], rounds::Bool=true) where {T<:AbstractVector{Float64}}
```

引数

  * Hamiltionian::Function: 三次元波数 `k` を引数とするハミルトニアン行列。
  * N::Int=10: ブリルアンゾーンを離散化する際のメッシュの数。$n$回目の反復はブリルアンゾーンを $1/N^n$ に分割します。
  * gapless<:AbstractVector{Float64}: 状態が重複するかどうかを決定する閾値。$n$回目の反復はベクトルの$n$番目の値の閾値を採用します。反復の回数はベクトルの長さによって変えることができます。
  * rounds::Bool=true: トポロジカル数の値を整数値に丸めるオプション。トポロジカル数は `true` の場合は `Int` 型の値を返し、`false` の場合は `Float` 型の値を返します。
