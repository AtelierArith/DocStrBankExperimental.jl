```
lobatto(N::Int,α::AbstractVector{<:Real},β::AbstractVector{<:Real},endl::Real,endr::Real)
lobatto(α::AbstractVector{<:Real},β::AbstractVector{<:Real},endl::Real,endr::Real)
lobatto(N::Int,op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},endl::Real,endr::Real)
lobatto(op::Union{OrthoPoly,AbstractCanonicalOrthoPoly},endl::Real,endr::Real)
```

ガウス・ロバット数値積分法。関連する直交多項式の再帰係数によってエンコードされた重み関数が与えられると、この関数は、重み関数に対する `(N+2)` 点のガウス・ロバット数値積分法のノードと重みを生成します。ここで、2つの指定されたノード `endl`、`endr`（通常はサポート区間の左端と右端、またはその左側および右側の点）があります。

!!! note
    関数 `radau` は、入力として最大 `N = length(α) - 3` を受け入れるため、最大で `(length(α) - 1)` 点の数値積分法を提供します。


!!! note
    参考文献: OPQ: A MATLAB SUITE OF PROGRAMS FOR GENERATING ORTHOGONAL POLYNOMIALS AND RELATED QUADRATURE RULES by Walter Gautschi

