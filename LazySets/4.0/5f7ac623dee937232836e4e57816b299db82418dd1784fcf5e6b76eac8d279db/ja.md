```
AbstractBallp{N} <: AbstractCentrallySymmetric{N}
```

p-ノルムボールのための抽象型。

### 注意事項

このインターフェースの標準実装については、[`Ballp`](@ref)を参照してください。

すべての具体的な`AbstractBallp`は、以下のメソッドを定義する必要があります：

  * `ball_norm(::AbstractBallp)` – 特性ノルムを返す
  * `radius_ball(::AbstractBallp)` – ボールの半径を返す

`AbstractBallp`のサブタイプ：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractBallp)
2-element Vector{Any}:
 Ball2
 Ballp
```

`AbstractBallp`インターフェースを実装するさらに2つのセットタイプがありますが、これらは他のインターフェースも実装しているため、サブタイプにはなれません：`Ball1`と`BallInf`。
