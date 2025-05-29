```
    MXH(pr::AbstractVector{<:Real}, pz::AbstractVector{<:Real}, R0::Real, Z0::Real, a::Real, b::Real, MXH_modes::Integer;
         optimize_fit=false, spline=false)
```

ミラー拡張調和表現のためのフーリエ係数を計算します：

```
R(θ) = R0 + R0*ϵ*cos(θᵣ(θ)) ただし θᵣ(θ) = θ + c0 + sum[c[m]*cos(m*θ) + s[m]*sin(m*θ)]
Z(θ) = Z0 - κ*R0*ϵ*sin(θ)
```

ここで、pr,pzはフラックス表面座標であり、MXH*modesはモードの数です。`optimize*fit`キーワードは、フィットパラメータを最適化して点を最もよく通過させることを示し、`spline`キーワードはモードのスプライン積分を使用することを示します。

N.B.: `optimize_fit`がfalseの場合、いくつかのMXH値は固定されます。すなわち、R0=R0、Z0=Z0、ϵ=a/R0、およびκ=b/aです。そうでなければ、これらは最適化のための開始値に過ぎません。
