```
抽象型 AbstractValueShape
```

`AbstractValueShape` は型とサイズ情報を組み合わせたものです。

スカラーの形状（[`ScalarShape`](@ref)を参照）、配列（[`ArrayShape`](@ref)を参照）、定数値（[`ConstValueShape`](@ref)を参照）、および `NamedTuple`（[`NamedTupleShape`](@ref)を参照）のためにサブタイプが定義されています。

`AbstractValueShape` のサブタイプは、`eltype`、`size`、および [`totalndof`](@ref) をサポートする必要があります。

値の形状は、未定義の内容を持つ指定された形状の値を生成するためのコンストラクタとして使用できます。形状の要素型が抽象型またはユニオン型である場合、適切な具体型が自動的に選択されます（[`ValueShapes.default_datatype`](@ref）を参照）：

```julia
shape = ArrayShape{Real}(2,3)
A = shape(undef)
typeof(A) == Array{Float64,2}
size(A) == (2, 3)
valshape(A) == ArrayShape{Float64}(2,3)
```

使用方法

```
(shape::AbstractValueShape)(data::AbstractVector{<:Real})::eltype(shape)
```

を使用して、匿名の実数値のフラットベクターを指定された形状の値として表示します：

```julia
data = [1, 2, 3, 4, 5, 6]
shape(data) == [1 3 5; 2 4 6]
```

その結果、

```
Base.Vector{<:Real}(undef, shape::AbstractValueShape)
```

は、指定された形状のためにそのようなフラットデータを保持するのに適した初期化されていないベクターを作成します。型 `T` が指定されていない場合、適切なデータ型が自動的に選択されます。

フラットデータの複数のベクターを扱う場合は、

```
shape.(data::ArraysOfArrays.AbstractVectorOfSimilarVectors)
```

を使用します。

ValueShapes は、特化したブロードキャスティングを介してこれをサポートします。

その結果、

```
ArraysOfArrays.VectorOfSimilarVectors{<:Real}(shape::AbstractValueShape)
```

は、指定された形状のためにフラットデータを保持できるベクターの適切なベクター（長さゼロ）を作成します。結果は、2次元の `ElasticArray` にラップされた `VectorOfSimilarVectors` になります。このようにして、すべてのデータは単一の連続したメモリチャンクに格納されます。

`AbstractValueShape` は `<=` および `>=` で比較でき、セマンティクスは型を `<:` および `>:` で比較するのに似ています：

```julia
a::AbstractValueShape <= b::AbstractValueShape == true
```

は、形状 `a` の値が形状 `b` の値を期待するコンテキストで使用できることを意味します。例えば：

```julia
(ArrayShape{Float64}(4,5) <= ArrayShape{Real}(4,5)) == true
(ArrayShape{Float64}(4,5) <= ArrayShape{Integer}(4,5)) == false
(ArrayShape{Float64}(2,2) <= ArrayShape{Float64}(3,3)) == false
(ScalarShape{Real}() >= ScalarShape{Int}()) == true
```
