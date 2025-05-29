```
geometricweight(a::Sequence{<:SequenceSpace})
```

`a`の係数の絶対値の対数に対して通常の最小二乗法を実行することによって、`a`の幾何学的減衰率の近似を計算します。

関連情報: [`GeometricWeight`](@ref), [`IdentityWeight`](@ref), [`AlgebraicWeight`](@ref), [`algebraicweight`](@ref) および [`BesselWeight`](@ref).

# 例

```jldoctest
julia> rate(geometricweight(Sequence(Taylor(10), [inv(2.0^i) for i in 0:10]))) ≈ 2
true

julia> rate.(geometricweight(Sequence(Taylor(10) ⊗ Fourier(3, 1.0), vec([inv(2.0^i * 3.0^abs(j)) for i in 0:10, j in -3:3])))) .≈ (2, 3)
(true, true)
```
