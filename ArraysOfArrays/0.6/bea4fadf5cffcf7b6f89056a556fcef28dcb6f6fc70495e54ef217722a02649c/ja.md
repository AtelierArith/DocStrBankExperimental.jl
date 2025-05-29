```
ArrayOfSimilarArrays{T,M,N,L,P} <: AbstractArrayOfSimilarArrays{T,M,N}
```

は、次元 `L = M + N` の配列のビューを、次元 M の配列として、要素が次元 N の配列であるように表します。すべての要素配列は暗黙的に同じサイズ/軸を持ちます。

コンストラクタ:

```
ArrayOfSimilarArrays{T,M,N}(flat_data::AbstractArray)
ArrayOfSimilarArrays{T,M}(flat_data::AbstractArray)
```

次の型エイリアスが定義されています:

  * `VectorOfSimilarArrays{T,M} = AbstractArrayOfSimilarArrays{T,M,1}`
  * `ArrayOfSimilarVectors{T,N} = AbstractArrayOfSimilarArrays{T,1,N}`
  * `VectorOfSimilarVectors{T} = AbstractArrayOfSimilarArrays{T,1,1}`

`VectorOfSimilarArrays` は、基になる配列がその最終次元のサイズ変更をサポートしている場合（例: `ElasticArray`）、`push!()` などをサポートします。

ネストされた配列は、関数 [`nestedview`](@ref) を使用して作成することもでき、ラップされたフラット配列はその後 [`flatview`](@ref) を使用してアクセスできます:

```julia
A_flat = rand(2,3,4,5,6)
A_nested = nestedview(A_flat, 2)
A_nested isa AbstractArray{<:AbstractArray{T,2},3} where T
flatview(A_nested) === A_flat
```
