```
HPolytope{N, VN<:AbstractVector{N}} <: AbstractPolytope{N}
```

制約表現における凸多面体を表す型、すなわち、有限の半空間の交差によって特徴付けられる有界集合、

$$
P = ⋂_{i = 1}^m H_i,
$$

ここで各 $H_i = \{x ∈ ℝ^n : a_i^T x ≤ b_i \}$ は半空間であり、$a_i ∈ ℝ^n$ は $i$-番目の半空間の法線ベクトル、$b_i$ は変位です。$P$ が有界であると仮定します（この仮定を行わない [`LazySets.HPolyhedron`](@ref) も参照してください）。

### フィールド

  * `constraints`       – 線形制約のベクトル
  * `check_boundedness` – （オプション、デフォルト: `false`）多面体が有界であるかどうかを確認するためのフラグ；（有界性はこの型の前提条件です）

### 注意事項

多面体は有界多面体です。

有界性はこの型の前提条件です。パフォーマンス上の理由から、コンストラクタではデフォルトで有界性はチェックされません。この仮定を利用するため、有界性のチェックは期待する答えを返さない場合があります。

```jldoctest isbounded
julia> P = HPolytope([HalfSpace([1.0], 1.0)]);  # x <= 1

julia> isbounded(P)  # 型の仮定を使用し、実際にはチェックしない
true

julia> isbounded(P, false)  # 実際の有界性チェックを行う
false
```
