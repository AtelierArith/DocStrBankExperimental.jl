```
abstract type StaticArray{S, T, N} <: AbstractArray{T, N} end
StaticScalar{T}     = StaticArray{Tuple{}, T, 0}
StaticVector{N,T}   = StaticArray{Tuple{N}, T, 1}
StaticMatrix{N,M,T} = StaticArray{Tuple{N,M}, T, 2}
```

`StaticArray`は、固定された既知のサイズを持つJuliaの配列です。

## 開発ドキュメント

以下のメソッドを定義する必要があります：

  * フラットなタプルのデータを受け取るコンストラクタ。
  * 整数（線形インデックス）を使った`getindex()`（可能であれば`@inline`と`@boundscheck`を使用）。
  * フラットなタプルのデータを返す`Tuple()`。

以下を実装することが有用かもしれません：

  * `similar_type(::Type{MyStaticArray}, ::Type{NewElType}, ::Size{NewSize})`、フラットなタプルのデータを受け取る型（または型コンストラクタ）を返します。

可変コンテナの場合、以下も定義する必要があるかもしれません：

  * 単一要素（線形インデックス）のための`setindex!`。
  * `similar(::Type{MyStaticArray}, ::Type{NewElType}, ::Size{NewSize})`。
  * 場合によっては、初期化されていないデータのためのゼロパラメータコンストラクタ`MyStaticArray{...}()`が存在することが想定されます。

（`SVector`、`SMatrix`、`SArray`、`MVector`、`MMatrix`、`MArray`、`SizedArray`、`FieldVector`、`FieldMatrix`、`FieldArray`も参照してください）
