```
PSO(f, population, k_max; w=1, c1=1, c2=1)
PSO(logger::Logbook, f, population, k_max; w=1, c1=1, c2=1)
```

## 引数

  * `f::Function`: **最小化**する目的関数。
  * `population::Vector{Particle}`: [`Particle`](@ref) 個体のリスト。
  * `k_max::Integer`: イテレーションの数。

## キーワード

  * `w`: 慣性重み。オプション、デフォルトは 1。
  * `c1`: 認知係数（自分の位置）。オプション、デフォルトは 1。
  * `c2`: 社会係数（他者の位置）。オプション、デフォルトは 1。

[`Result`](@ref) を返します。
