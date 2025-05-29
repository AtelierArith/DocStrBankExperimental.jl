```
contact_constraint(bodies::Vector{Body}) 

リスト内の各Bodyに対してContactConstraintsを生成します

normals: 各接触点の表面法線
friction_coefficients: 各接触点の摩擦係数の値（ImpactContactにはオプション）
contact_origins: 各接触点に対するBodyの中心からのオフセット（オプション）
contact_radius: 各接触の半径（オプション）
contact_type: :nonlinear, :linear, :impact
```
