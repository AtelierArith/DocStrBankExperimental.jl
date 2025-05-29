```
AbstractArrayOfSimilarArrays{T,M,N} <: AbstractArray{<:AbstractArray{T,M},N}
```

同じサイズ/軸を持つ配列を含む配列です。この配列は内部的に次元 `M + N` の何らかの配列としてフラットな形式で保存されます。フラットな形式には `flatview(A)` を介してアクセスできます。

サブタイプは（典型的な配列操作に加えて）以下を実装する必要があります：

```
flatview(A::SomeArrayOfSimilarArrays)::AbstractArray{T,M+N}
```

以下の型エイリアスが定義されています：

  * `AbstractVectorOfSimilarArrays{T,M} = AbstractArrayOfSimilarArrays{T,M,1}`
  * `AbstractArrayOfSimilarVectors{T,N} = AbstractArrayOfSimilarArrays{T,1,N}`
  * `AbstractVectorOfSimilarVectors{T} = AbstractArrayOfSimilarArrays{T,1,1}`
