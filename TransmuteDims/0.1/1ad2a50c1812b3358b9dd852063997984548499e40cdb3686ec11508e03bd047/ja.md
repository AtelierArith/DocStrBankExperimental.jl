```
transmutedims(A, perm⁺)
```

これは、常に `DenseArray` を返す [`transmute`](@ref) のイagerバージョンですが、データをコピーすることは保証されていません。

`transmute` と同様に、`PermutedDimsArray`、`Transpose{<:Number}` などをアンラップすることを知っています。

`transmute` と [`TransmutedDimsArray`](@ref) の両方と同様に、摂動に加えて、`1:ndims(A)` の外の値（トリビアルな次元を挿入します）、省略された値（`dropdims` のようにサイズ1の次元でなければなりません）、および繰り返された値（`diagm` を一般化します）を受け入れます。

# 例

```jldoctest; setup=:(using TransmuteDims)
julia> A = transmutedims(reshape(1:15,3,5), (3,2,1))  # A は新しい配列です
1×5×3 Array{Int64, 3}:
[:, :, 1] =
 1  4  7  10  13

[:, :, 2] =
 2  5  8  11  14

[:, :, 3] =
 3  6  9  12  15

julia> B = transmutedims(A, (2,3))  # A の最初のトリビアルな次元を削除します
5×3 Matrix{Int64}:
  1   2   3
  4   5   6
  7   8   9
 10  11  12
 13  14  15

julia> C = transmutedims(adjoint(B), (2,1,0)); summary(C)  # アジョイントをアンラップします
"5×3×1 Array{Int64, 3}"

julia> D = transmutedims(adjoint(B), (1,0,2)); summary(D)  # アンラップしてから順序を変更します
"3×1×5 Array{Int64, 3}"

julia> B[5,3] = 5030;  # B と C は A の再形成されたビューです

julia> A[1,5,3]
5030

julia> C[5,3,1]
5030

julia> D[3,1,5]  # しかし D はそうではなく、コピーが必要でした
15

julia> transmutedims((1, 2, 3.0, 4+5im))  # デフォルトの perm = (0,1) はベクトル（およびタプル）用です
1×4 Matrix{Number}:
 1  2  3.0  4+5im

julia> transmutedims(B)  # デフォルトの perm = (2,1) は行列用です
3×5 Matrix{Int64}:
 1  4  7  10    13
 2  5  8  11    14
 3  6  9  12  5030
```
