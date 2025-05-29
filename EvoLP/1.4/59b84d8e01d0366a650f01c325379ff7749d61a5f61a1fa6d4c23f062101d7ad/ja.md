```
oneplusone(f, ind, k_max, M)
oneplusone(logger::Logbook, f, ind, k_max, M)
```

1+1進化アルゴリズム。

# 引数

  * `f::Function`: **最小化**する目的関数。
  * `ind::AbstractVector`: 進化を開始する個体。
  * `k_max::Integer`: 繰り返しの回数。
  * `M::Mutator`: 利用可能な[`Mutator`](@ref)の1つ。

[`Result`](@ref)を返します。
