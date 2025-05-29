```julia
mutable struct Buffer{M<:Causal.BufferMode, T, N} <: AbstractArray{T, N}
```

サイズ `sz` の `Buffer` を要素型 `T` で構築します。`M` は `Buffer` のモードで、データの読み書き方法を決定します。異なるバッファモードが存在します：

  * `Normal`: [`Normal`](@ref) を参照
  * `Cyclic`: [`Cyclic`](@ref) を参照
  * `Lifo`: [`Lifo`](@ref) を参照
  * `Fifo`: [`Fifo`](@ref) を参照

`Buffer` のデフォルトモードは `Cyclic` で、デフォルトの要素型は `Float64` です。

```
Buffer{M}(sz::Int...) where {M, T}
```

サイズ `sz` で要素型 `T` とモード `M` の `Buffer` を構築します。

```
Buffer(dtype::Type{T}, sz::Int...) where T
```

サイズ `sz` で要素型 `T` の `Buffer` を構築します。バッファのモードは `Cyclic` です。

```
Buffer(sz::Int...)
```

サイズ `sz` でモード `Cyclic` と要素型 `Float64` の `Buffer` を構築します。

```
Buffer{M}(data::AbstractVecOrMat{T}) where {M, T<:Real}
```

`data` で `Buffer` を構築します。

# フィールド

  * `internals::Array{Array{T, N}, 1} where {T, N}`: 内部データコンテナ
  * `src::Int64`: 入力コンテナ
  * `dst::Int64`: 出力コンテナ
  * `index::Int64`: バッファインデックス
  * `state::Symbol`: バッファの現在の状態。:full, :empty, :nonempty のいずれか
  * `id::Base.UUID`: 一意の識別子

# 例

```jldoctest
julia> buf = Buffer(5)
5-element Buffer{Cyclic,Float64,1}

julia> buf = Buffer{Fifo}(2, 5)
2×5 Buffer{Fifo,Float64,2}

julia> buf = Buffer{Lifo}(collect(reshape(1:8, 2, 4)))
2×4 Buffer{Lifo,Int64,2}
```
