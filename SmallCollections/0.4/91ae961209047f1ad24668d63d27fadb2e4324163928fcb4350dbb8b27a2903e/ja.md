```
PackedVector{U<:Unsigned,M,T<:Union{Base.BitInteger,Bool}} <: AbstractCapacityVector{T}

PackedVector{U,M,T}()
PackedVector{U,M,T}(iter)
PackedVector{U,M}(v::AbstractVector{T})
PackedVector{U,M}(t::Tuple)
PackedVector(v::AbstractSmallVector{M,T})
```

この不変ベクトルのタイプは、各エントリに対して `M` ビットのタイプ `U` の共通ビットマスクに要素を格納します。許可される値の範囲は、`T <: Signed` の場合は `-2^(M-1):2^(M-1)-1`、`T <: Unsigned` の場合は `0:2^M-1`、`T == Bool` の場合は `false:true` です。それ以外に、公式の要素タイプ `T` はエントリを取得する際にのみ使用されます。容量、すなわち格納できる要素の数は `bitsize(U)÷M` で与えられます。

`AbstractVector` またはタプルから `PackedVector` を作成する際に、要素タイプ `T` は省略できます。後者の場合、`T` はタプルの要素タイプを昇格させることによって決定されます。引数が与えられない場合、空のベクトルが返されます。`AbstractSmallVector` `v` から `PackedVector` が作成され、パラメータ `U` と `M` が省略されると、`M` は `bitsize(T)` に設定され、`U` は結果のベクトルの容量が `v` の容量以上になるように選ばれます。

ベクトルの加算または減算中のオーバーフローやアンダーフローはエラーをスローしません。同様に、タイプ `T` のスカラーによる乗算にも当てはまります。他のタイプによるスカラー乗算は `Vector` を返します。

`SmallVector` と比較して、`PackedVector` は挿入および削除操作が速い場合があります。算術演算は通常遅くなりますが、`M` がハードウェア整数のサイズである場合はその限りではありません。

[`capacity`](@ref capacity(::Type{<:PackedVector})), [`SmallCollections.bitsize`](@ref) も参照してください。

# 例

```jldoctest
julia> v = PackedVector{UInt64,5,Int8}(-5:5:10)
4-element PackedVector{UInt64, 5, Int8}:
 -5
  0
  5
 10

julia> capacity(v)
12

julia> w = PackedVector{UInt64,5,Int8}([1, 2, 3, 4])
4-element PackedVector{UInt64, 5, Int8}:
 1
 2
 3
 4

julia> v+w
4-element PackedVector{UInt64, 5, Int8}:
 -4
  2
  8
 14

julia> Int8(2)*v
4-element PackedVector{UInt64, 5, Int8}:
 -10
   0
  10
 -12
```
