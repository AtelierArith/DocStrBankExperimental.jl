```julia
abstract type Heuristic
```

探索ヒューリスティックのための抽象型で、`State`から指定された目標までの距離を推定します [`Specification`](@ref)。構築された後、`heuristic`はドメイン、状態、および仕様に対して呼び出され、`Real`数（通常はメモリ使用量を削減するために`Float32`）を返します。

```
heuristic(domain, state, spec; precompute=true)
```

ヒューリスティックは、検索中に繰り返し使用される情報を事前に計算して保存することがあります [`precompute!`](@ref) メソッドを介して。状態に対するヒューリスティックの評価は[`compute`](@ref)によって定義されます。

`heuristic`を関数として呼び出す際に`precompute`キーワード引数がtrueの場合、[`compute`](@ref)が呼び出される前に[`precompute!`](@ref)が呼び出されてヒューリスティック評価が行われます。
