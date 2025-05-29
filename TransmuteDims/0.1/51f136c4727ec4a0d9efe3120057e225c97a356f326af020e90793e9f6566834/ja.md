```
transmute(A, perm⁺)
transmute(A, Val(perm⁺))
```

は結果 `== TransmutedDimsArray(A, perm⁺)` を返しますが：

  * `A` が `PermutedDimsArray`、`Transpose{<:Number}`、`Adjoint{<:Real}`、または `Diagonal` の場合、これをアンラップし、`perm⁺` を `parent(A)` に直接作用するように調整します。
  * 順列が単にトリビアルな次元を挿入または削除する場合、ラッピングする代わりに `reshape` を優先します。これは `may_reshape(::Type)` によって制御されており、デフォルトでは `DenseArray` と `ReshapedArray` に対して真です。
  * 可能な場合、`TransmutedDimsArray` の代わりに `Transpose` または `Diagonal` を作成することを優先します。
  * 順列が `Val` にラップされている場合、その逆を計算する（およびサニティチェックを行う）ことは常にコンパイル時に行われます。

# 例

```jldoctest; setup=:(using TransmuteDims, Random; Random.seed!(42);)
julia> A = transpose(rand(Int8, 4, 2))
2×4 transpose(::Matrix{Int8}) with eltype Int8:
 115    99  0  57
  88  -105  3  76

julia> B = transmute(A, (3,2,1))  # transposeをアンラップし、その後reshape
1×4×2 Array{Int8, 3}:
[:, :, 1] =
 115  99  0  57

[:, :, 2] =
 88  -105  3  76

julia> B == TransmutedDimsArray(A, (0,2,1))  # 同じ値、異なる型
true

julia> transmute(A, (2,2,0,1))
4×4×1×2 transmute(::Matrix{Int8}, (1, 1, 0, 2)) with eltype Int8:
[:, :, 1, 1] =
 115   ⋅  ⋅   ⋅
   ⋅  99  ⋅   ⋅
   ⋅   ⋅  0   ⋅
   ⋅   ⋅  ⋅  57

[:, :, 1, 2] =
 88     ⋅  ⋅   ⋅
  ⋅  -105  ⋅   ⋅
  ⋅     ⋅  3   ⋅
  ⋅     ⋅  ⋅  76

julia> ans == transmute(B, (2,2,1,3))
true

julia> TransmuteDims.may_reshape(typeof(A))  # ラッピングのreshapeを避ける
false

julia> TransmuteDims.may_reshape(typeof(B))
true

julia> transmute(('α', "β", :γ), (2,1))  # タプルも受け入れる
1×3 transmute(TupleVector(::Tuple{Char, String, Symbol}), (0, 1)) with eltype Any:
 'α'  "β"  :γ
```
