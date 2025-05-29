```
overapproximate(X::LazySet, ZT::Type{<:Zonotope},
                dir::Union{AbstractDirections, Type{<:AbstractDirections}};
                [algorithm]="vrep", kwargs...)
```

ゾノトープで集合を過大評価します。

### 入力

  * `X`         – 集合
  * `Zonotope`  – 目標集合の型
  * `dir`       – ジェネレーターに使用される方向
  * `algorithm` – （オプション、デフォルト: `"vrep"`）過大評価を計算するために使用されるアルゴリズム
  * `kwargs`    – その他のアルゴリズム特有のオプション

### 出力

`X`を過大評価し、`dir`で提供されたジェネレーター方向を最大限に使用するゾノトープ（冗長な方向は無視されます）。

### 注意事項

2つのアルゴリズムが利用可能です：

  * `"vrep"` – 与えられた方向のジェネレーターのみを使用して、最小の総ジェネレーター和を持つゾノトープで多面体集合を過大評価します。この制約の下で、ゾノトープはジェネレーターベクトルの最小和を持ちます。詳細については、[`_overapproximate_zonotope_vrep`](@ref)のドキュメントを参照してください。
  * `"cpa"` – 2次元ブロックへの直交分解を使用して、ゾノトープで多面体集合を過大評価します。詳細については、[`_overapproximate_zonotope_cpa`](@ref)のドキュメントを参照してください。
