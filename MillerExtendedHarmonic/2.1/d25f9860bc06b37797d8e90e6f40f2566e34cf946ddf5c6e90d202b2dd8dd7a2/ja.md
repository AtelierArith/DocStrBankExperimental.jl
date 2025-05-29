```
MXH(
pr::AbstractVector{<:Real},
pz::AbstractVector{<:Real},
MXH_modes::Integer=5;
optimize_fit=false,
spline=false,
rmin=0.0,
rmax=0.0,
zmin=0.0,
zmax=0.0)
```

ミラー拡張ハーモニック表現のためのフーリエ係数を計算します：

```
R(θ) = R0 + R0*ϵ*cos(θᵣ(θ)) ただし θᵣ(θ) = θ + c0 + sum[c[m]*cos(m*θ) + s[m]*sin(m*θ)]
Z(θ) = Z0 - κ*R0*ϵ*sin(θ)
```

ここで、pr,pzはフラックス表面座標であり、MXH*modesはモードの数です。`optimize*fit`キーワードは、フィットパラメータを最適化してポイントを最もよく通過させることを示します。`spline`キーワードは、モードのスプライン積分を使用することを示します。`rmin`,`rmax`,`zmin`,`zmax`はフィットのための特定の最大値と最小値を強制します。
