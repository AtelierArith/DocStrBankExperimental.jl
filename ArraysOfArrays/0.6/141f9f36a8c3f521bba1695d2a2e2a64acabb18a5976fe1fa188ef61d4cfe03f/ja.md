```
VectorOfArrays{T,N,M} <: AbstractVector{<:AbstractArray{T,N}}
```

`VectorOfArrays`は、サイズが異なる可能性のある`N`次元配列のベクトルを表します。内部的に、`VectorOfArrays`はすべての配列のすべての要素を単一のフラットベクトルに格納します。`M`は`N - 1`に等しくなければなりません。

`VectorOfArrays`自体は`push!`、`unshift!`などをサポートしていますが、ベクトル内の各個別配列のサイズは固定です。`resize!`は縮小に使用できますが、成長には使用できません。なぜなら、ベクトル内の追加要素配列のサイズは不明だからです。ただし、最大サイズ`s`の`n`個の配列のためのメモリ空間は、`sizehint!(A::VectorOfArrays, n, s::Dims{N})`を介して予約できます。

コンストラクタ:

```julia
VectorOfArrays{T,N}()

VectorOfArrays(A::AbstractVector{<:AbstractArray})
VectorOfArrays{T}(A::AbstractVector{<:AbstractArray})
VectorOfArrays{T,N}(A::AbstractVector{<:AbstractArray})

VectorOfArrays(
    data::AbstractVector,
    elem_ptr::AbstractVector{<:Integer},
    kernel_size::AbstractVector{<:Dims}
    checks::Function = ArraysOfArrays.full_consistency_checks
)
```

`checks`に適した他の値は、`ArraysOfArrays.simple_consistency_checks`および`ArraysOfArrays.no_consistency_checks`です。

`VectorOfVectors`は型エイリアスとして定義されています:

```julia
`VectorOfVectors{T,VT,VI,VD} = VectorOfArrays{T,1,VT,VI,VD}`
```
