```
algebraicweight(a::Sequence{<:SequenceSpace})
```

`a`の係数の絶対値の対数に対して通常の最小二乗法を実行することによって、`a`の代数的減衰率の近似値を計算します。

関連情報: [`AlgebraicWeight`](@ref), [`IdentityWeight`](@ref), [`GeometricWeight`](@ref), [`geometricweight`](@ref) および [`BesselWeight`](@ref).

# 例

```jldoctest
julia> rate(algebraicweight(Sequence(Taylor(10), [inv((1.0 + i)^2) for i in 0:10]))) ≈ 2
true

julia> rate.(algebraicweight(Sequence(Taylor(10) ⊗ Fourier(3, 1.0), vec([inv((1.0 + i)^2 * (1.0 + abs(j))^3) for i in 0:10, j in -3:3])))) .≈ (2, 3)
(true, true)
```
