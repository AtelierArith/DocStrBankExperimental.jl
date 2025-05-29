```
fsparse(I::Tuple, V,[ M::Tuple, combine]; fill_value=zero(eltype(V)))
```

スパース COO テンソル `S` を作成します。`size(S) == M` であり、`S[(i[q] for i = I)...] = V[q]` となります。combine 関数は重複を結合するために使用されます。`M` が指定されていない場合、`M` は `map(maximum, I)` に設定されます。combine 関数が指定されていない場合、combine はデフォルトで `+` になりますが、`V` の要素がブール値の場合は combine はデフォルトで `|` になります。`I` のすべての要素は 1 <= I[n][q] <= M[n] を満たさなければなりません。数値のゼロは構造的な非ゼロとして保持されます。数値のゼロを削除するには、dropzeros! を使用してください。

参照: [`sparse`](https://docs.julialang.org/en/v1/stdlib/SparseArrays/#SparseArrays.sparse)

# 例

julia> I = (     [1, 2, 3],     [1, 2, 3],     [1, 2, 3]);

julia> V = [1.0; 2.0; 3.0];

julia> fsparse(I, V) SparseCOO (0.0) [1:3×1:3×1:3] │ │ │ └─└─└─[1, 1, 1] [2, 2, 2] [3, 3, 3]       1.0       2.0       3.0 ```
