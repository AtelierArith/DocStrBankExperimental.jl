```
Log([λ = 1])
```

相関長 `λ` と分散 `σ² = ∞` を持つ対数共分散関数。

ガウス乗法的カオスを生成するために使用されます。

これは $C(r) = \log\left(\frac{\lambda}{r}\right)$ と定義されます。

# 例

```jldoctest
julia> logcov = Log(1.5)
Log{Float64}(λ=1.5)

julia> logcov(0)
Inf

julia> logcov(1.5)
0.0
```
