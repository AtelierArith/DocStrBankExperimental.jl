```
TransmutedDimsArray(A, perm⁺)
```

これは `PermutedDimsArray` と似ていますが、`perm⁺` は必ずしも置換である必要はありません：

  * `0` を含む場合、出力にサイズ1のトリビアルな次元が挿入されます。`1:ndims(A)` の範囲外のものはすべて `0` として扱われます - `size(A,99) == 1` に適合しますが、`nothing` も許可されます。
  * `perm⁺` から省略された任意の数は、サイズ1である必要がある次元として削除されます。
  * `perm⁺` に同じ数が2回現れると、その次元では結果が `Diagonal` のように動作します。

型を直接呼び出すことで最も単純なコンストラクタを得ることができます。代わりに [`transmute(A, perm⁺)`](@ref) を呼び出すと、ネストされたオブジェクトをアンラップし、より単純な代替を選択するものが得られます。また、[`transmutedims(A, perm⁺)`](@ref) は即時バージョンです。

# 例

```jldoctest; setup=:(using TransmuteDims)
julia> TransmutedDimsArray('a':'e', (2,1))  # 転置のように
1×5 transmute(::StepRange{Char, Int64}, (0, 1)) with eltype Char:
 'a'  'b'  'c'  'd'  'e'

julia> TransmutedDimsArray('a':'e', (nothing, 1, nothing))  # 2つのトリビアルな次元
1×5×1 transmute(::StepRange{Char, Int64}, (0, 1, 0)) with eltype Char:
[:, :, 1] =
 'a'  'b'  'c'  'd'  'e'

julia> A = rand(10, 20, 30);

julia> B = TransmutedDimsArray(A, (3,0,1,2));  # reshape + permute のように

julia> size(B)
(30, 1, 10, 20)

julia> B[3,1,1,2] == A[1,2,3] == A[1,2,3,1]  # 暗黙の末尾次元
true

julia> B == TransmutedDimsArray(A, (3,4,1,2)) == permutedims(A[:,:,:,:], (3,4,1,2))
true

julia> TransmutedDimsArray(reshape(1:6,3,2), (1,1,2))  # 一般化された対角行列
3×3×2 transmute(reshape(::UnitRange{Int64}, 3, 2), (1, 1, 2)) with eltype Int64:
[:, :, 1] =
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

[:, :, 2] =
 4  ⋅  ⋅
 ⋅  5  ⋅
 ⋅  ⋅  6
```
