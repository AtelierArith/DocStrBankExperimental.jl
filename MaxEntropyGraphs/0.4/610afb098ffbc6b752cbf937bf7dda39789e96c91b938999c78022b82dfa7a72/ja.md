```
L_BiCM_reduced(θ::Vector, k⊥::Vector, k⊤::Vector, f⊥::Vector, f⊤::Vector, nz⊥::UnitRange, nz⊤::UnitRange, n⊥ᵣ::Int)
```

縮小されたBiCMモデルの対数尤度を指数形式で計算し、凸性を維持します。

# 引数

  * `θ`: モデルの最尤パラメータ ([α; β])
  * `k⊥`: ⊥層の縮小された次数列
  * `k⊤`: ⊤層の縮小された次数列
  * `f⊥`: ⊥層の各次数の頻度
  * `f⊤`: ⊤層の各次数の頻度
  * `nz⊥`: 縮小された⊥層次数列の非ゼロ要素のインデックス
  * `nz⊤`: 縮小された⊤層次数列の非ゼロ要素のインデックス
  * `n⊥ᵣ`: 縮小された⊥層次数列のユニークな値の数

この関数は、縮小されたモデルの対数尤度を返します。最適化のために、この関数は特定のモデルに関連付けられた匿名関数を生成するために使用されます。

# 例

```jldoctest
# 一般的な使用法:
julia> k⊥ = [1, 2, 3, 4];

julia> k⊤  = [1, 2, 4];

julia> f⊥  = [1; 3; 1; 1];

julia> f⊤  = [4; 2; 1];

julia> nz⊥ = 1:length(k⊥);

julia> nz⊤ = 1:length(k⊤);

julia> n⊥ᵣ = length(k⊥);

julia> θ   = collect(range(0.1, step=0.1, length=length(k⊥) + length(k⊤)));

julia> L_BiCM_reduced(θ, k⊥, k⊤, f⊥, f⊤, nz⊥, nz⊤, n⊥ᵣ)
-26.7741690720244
```

```jldoctest
# DBCMモデルとの併用:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> model_fun = θ -> L_BiCM_reduced(θ, model.d⊥ᵣ, model.d⊤ᵣ, model.f⊥, model.f⊤, model.d⊥ᵣ_nz, model.d⊤ᵣ_nz, model.status[:d⊥_unique]);

julia> model_fun(ones(size(model.θᵣ)))
-237.5980041411147
```
