すべての状態推定器の抽象スーパークラス。

---

```
(estim::StateEstimator)(d=[]) -> ŷ
```

[`evaloutput`](@ref) のエイリアスとして呼び出し可能な `StateEstimator` オブジェクトを許可するファンクタ。

# 例

```jldoctest
julia> kf = KalmanFilter(setop!(LinModel(tf(3, [10, 1]), 2), yop=[20]), direct=false);

julia> ŷ = kf() 
1-element Vector{Float64}:
 20.0
```
