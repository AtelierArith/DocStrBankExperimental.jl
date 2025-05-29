```
HPolyhedron{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

制約表現における凸多面体を表す型であり、すなわち半空間の有限な交差である。

$$
P = ⋂_{i = 1}^m H_i,
$$

ここで各 $H_i = \{x ∈ ℝ^n : a_i^T x ≤ b_i \}$ は半空間であり、$a_i ∈ ℝ^n$ は $i$-番目の半空間の法線ベクトル、$b_i$ は変位です。集合 $P$ は有界である場合とない場合があります（有界性を仮定する [`HPolytope`](@ref) も参照）。

### フィールド

  * `constraints` – 線形制約のベクトル
