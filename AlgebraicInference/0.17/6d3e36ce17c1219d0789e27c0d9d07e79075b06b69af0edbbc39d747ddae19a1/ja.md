```
GaussianSystem(
    P::AbstractMatrix,
    S::AbstractMatrix,
    p::AbstractVector,
    s::AbstractVector,
    σ::Real)
```

エネルギー関数を指定してガウス系を構築します。次のように設定する必要があります。

```julia
σ  = dot(s, pinv(S) * s)
```
