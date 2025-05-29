```
L_DBCM_reduced(θ::Vector, k_out::Vector, k_in::Vector, F::Vector, nz_out::Vector, nz_in::Vector, n::Int=length(k_out))
```

縮小されたDBCMモデルの対数尤度を指数形式で計算し、凸性を維持します。

# 引数

```
- `θ`: モデルの最尤パラメータ ([α; β])
- `k_out`: 縮小された出次数列
- `k_in`: 縮小された入次数列
- `F`: 次数列内の各ペアの頻度
- `nz_out`: 縮小された出次数列の非ゼロ要素のインデックス
- `nz_in`: 縮小された入次数列の非ゼロ要素のインデックス
- `n`: 縮小モデル内のノード数
```

この関数は、縮小モデルの対数尤度を返します。最適化のために、この関数は特定のモデルに関連付けられた無名関数を生成するために使用されます。

# 例

```jldoctest
# 一般的な使用法:
julia> k_out  = [1, 1, 1, 2, 2, 2, 3, 3, 4, 4, 4, 5, 5];

julia> k_in   = [2, 3, 4, 1, 3, 5, 2, 4, 1, 2, 4, 0, 4];

julia> F      = [2, 2, 1, 1, 1, 2, 3, 1, 1, 2, 2, 1, 1];

julia> θ      = collect(range(0.1, step=0.1, length=length(k_out)));

julia> nz_out = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13];

julia> nz_in  = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 13];

julia> n      = length(k_out);

julia> L_DBCM_reduced(θ, k_out, k_in, F, nz_out, nz_in, n);

```

```jldoctest
# DBCMモデルとの使用:
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> model_fun = θ -> L_DBCM_reduced(θ, model.dᵣ_out, model.dᵣ_in, model.f, model.dᵣ_out_nz, model.dᵣ_in_nz, model.status[:d_unique]);

julia> model_fun(ones(size(model.θᵣ)))
-252.4627226503138
```
