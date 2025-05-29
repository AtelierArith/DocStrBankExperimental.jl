```
FluxUpwind(splitting)
```

数値フラックス `f(u_left, u_right) = f⁺(u_left) + f⁻(u_right)` はフラックスベクトル分割に基づいています。

与えられた `splitting` を持つ [`SurfaceIntegralUpwind`](@ref) は、数値フラックスとして `FluxUpwind(splitting)` を持つ [`SurfaceIntegralStrongForm`](@ref) と同等です（浮動小数点の違いを除く）。なお、[`SurfaceIntegralUpwind`](@ref) は [`TreeMesh`](@ref) でのみ利用可能です。

!!! warning "実験的な実装 (アップウィンド SBP)"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

