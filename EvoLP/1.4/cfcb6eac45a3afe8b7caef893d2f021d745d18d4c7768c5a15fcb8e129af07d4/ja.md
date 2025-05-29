```
GA(f, pop, k_max, S, C, M)
GA(logbook::Logbook, f, population, k_max, S, C, M)
GA(notebooks::Vector{Logbook}, f, population, k_max, S, C, M)
```

世代遺伝的アルゴリズム。

## 引数

  * `f::Function`: **最小化**する目的関数。
  * `population::AbstractVector`: ベクトル個体のリスト。
  * `k_max::Integer`: 繰り返しの回数。
  * `S::ParentSelector`: 利用可能な [`ParentSelector`](@ref) の1つ。
  * `C::CrossoverMethod`: 利用可能な [`CrossoverMethod`](@ref) の1つ。
  * `M::MutationMethod`: 利用可能な [`MutationMethod`](@ref) の1つ。

[`Result`](@ref) を返します。
