```
radau(N::Int,α::AbstractVector{<:Real},β::AbstractVector{<:Real},end0::Real)
radau(α::AbstractVector{<:Real},β::AbstractVector{<:Real},end0::Real)
radau(N::Int,op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},end0::Real)
radau(op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},end0::Real)
```

ガウス-ラドー数値積分法。再帰係数 `(α,β)` で符号化された重み関数が与えられたとき、この関数は、指定されたノード `end0`（通常は w の支持区間の端点のいずれか、またはその外部）を持つ重み関数のための `(N+1)` 点ガウス-ラドー数値積分法のノードと重みを生成します。

!!! note
    関数 `radau` は、入力として最大 `N = length(α) - 2` を受け入れるため、最大で `(length(α) - 1)` 点の数値積分法を提供します。


!!! note
    参考文献: OPQ: A MATLAB SUITE OF PROGRAMS FOR GENERATING ORTHOGONAL POLYNOMIALS AND RELATED QUADRATURE RULES by Walter Gautschi

