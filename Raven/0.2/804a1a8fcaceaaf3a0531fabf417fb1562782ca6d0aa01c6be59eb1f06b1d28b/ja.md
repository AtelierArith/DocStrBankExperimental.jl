```
GridArray{T}(undef, grid::Grid)
```

グリッド内の各ポイント（ゴーストセルを含む）に対して、型 `T` の要素を含む配列を作成します。配列の次元は `(size(referencecell(grid))..., length(grid))` であり、ゴーストセルはデフォルトで隠されています。

型 `T` は `NTuple{M,L}` に解釈できると仮定されます。いくつかの例として（いくつかは `StructArrays` を使用）：

  * `T = NamedTuple{(:E,:B),Tuple{SVector{3,ComplexF64},SVector{3,ComplexF64}}}`
  * `T = NTuple{5,Int64}`
  * `T = SVector{5,Int64}`
  * `T = ComplexF32`
  * `T = Float32`

構造体の配列スタイルのストレージを使用する代わりに、GPU効率の良い配列の構造体スタイルのストレージが使用されます。例えば、データを次のように保存する代わりに

```julia-repl
julia> T = Tuple{Int,Int};
julia> data = Array{T}(undef, 3, 4, 2); a .= Ref((1,2))
3×4 Matrix{Tuple{Int64, Int64}}:
 (1, 2)  (1, 2)  (1, 2)  (1, 2)
 (1, 2)  (1, 2)  (1, 2)  (1, 2)
 (1, 2)  (1, 2)  (1, 2)  (1, 2)
```

データは次の順序で保存されます

```julia-repl
julia> permutedims(reinterpret(reshape, Int, data), (2,3,1,4))
3×4×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  1  1  1
 1  1  1  1
 1  1  1  1

[:, :, 2, 1] =
 2  2  2  2
 2  2  2  2
 2  2  2  2

[:, :, 1, 2] =
 1  1  1  1
 1  1  1  1
 1  1  1  1

[:, :, 2, 2] =
 2  2  2  2
 2  2  2  2
 2  2  2  2
```

`GridArray` の場合、`T` に関連付けられたインデックスの前のインデックス（上記の例では最初の2つ）はセルの自由度に関連付けられています。後の1つはセルの数に関連付けられています。
