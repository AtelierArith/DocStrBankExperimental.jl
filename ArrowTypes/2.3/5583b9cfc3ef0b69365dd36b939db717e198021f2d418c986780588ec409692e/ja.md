```
ArrowTypes.ArrowKind(T)
```

与えられた型 `T` に対して、その「矢印型の種類」を定義します。これは、扱うべき矢印型の一般的なカテゴリです。次のいずれかでなければなりません：

  * [`ArrowTypes.NullKind`](@ref): `Missing` は `NullKind` として定義された唯一の型です
  * [`ArrowTypes.PrimitiveKind`](@ref): `<:Integer`、`<:AbstractFloat`、`Arrow.Decimal`、およびさまざまな `Arrow.ArrowTimeType` サブタイプ
  * [`ArrowTypes.BoolKind`](@ref): `Bool` のみ
  * [`ArrowTypes.ListKind`](@ref): 任意の `AbstractString` または `AbstractArray`
  * [`ArrowTypes.FixedSizeList`](@ref): `NTuple{N, T}`
  * [`ArrowTypes.MapKind`](@ref): 任意の `AbstractDict`
  * [`ArrowTypes.StructKind`](@ref): 任意の `NamedTuple` または通常の構造体（可変またはそれ以外）
  * [`ArrowTypes.UnionKind`](@ref): 任意の `Union`
  * [`ArrowTypes.DictEncodedKind`](@ref): `DataAPI.refarray` インターフェースを実装する配列型

上記の `ArrowKind` のリストは、矢印データ形式によってサポートされるデータを物理的に保存するさまざまな方法に変換されます。カスタム型に適しているかどうかのアイデアについては、それぞれのドキュメントを参照してください。カスタム型は、さまざまな `ArrowKind` 型によって要求される追加の「インターフェースメソッド」を満たす必要があることに注意してください。デフォルトでは、julia で型が `primitive type ...` のように宣言されている場合、それは `PrimitiveKind` と見なされ、`struct` または `mutable struct` の場合は `StructKind` と見なされます。また、型は `ArrowKind` を定義する必要があることはまれであり、`ArrowType(T)` と `toarrow(x::T)` を定義して `T` をネイティブにサポートされる矢印型に変換することがはるかに一般的であり、その際にはすでに `ArrowKind` が定義されています。
