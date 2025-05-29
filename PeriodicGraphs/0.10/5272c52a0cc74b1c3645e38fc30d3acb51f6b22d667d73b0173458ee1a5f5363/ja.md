```
AbstractSymmetryGroup{T<:AbstractSymmetry}
```

グラフの対称性の集合を表す抽象型です。

## インターフェース

任意の `AbstractSymmetryGroup` 型は、`Base` 関数 `unique`、`iterate`、`length` および `one` のメソッドを定義しなければなりません。これにより、任意の `s` が型 `<: AbstractSymmetryGroup{T}` の場合：

  * `s(i)` は `i` の対称軌道上の代表であり、軌道上のすべての要素が同じ代表を共有します。代表は整数であるべきです。
  * `unique(s)` はそのような代表のイテレータです。
  * `s` を反復すると、対称操作 `symm` のリストが得られ、それぞれが型 `T` のオブジェクトとして表されます（ここで `T <:`[`AbstractSymmetry`](@ref) は `typeof(s)` のパラメータです）。恒等対称性は、特定の [`IncludingIdentity`](@ref) サブタイプの `AbstractSymmetryGroup` を除いて、これらの `symm` に含まれてはなりません。
  * `one(s)` は型 `T` の恒等対称性です。
