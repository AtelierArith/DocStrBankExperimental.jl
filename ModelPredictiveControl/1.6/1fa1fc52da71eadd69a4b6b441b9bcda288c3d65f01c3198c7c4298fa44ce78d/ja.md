```
evaloutput(estim::StateEstimator, d=[]) -> ŷ
```

`StateEstimator` の出力 `ŷ` を `estim.x̂0` の状態と外乱 `d` から評価します。

現在の時間ステップでの `estim` の出力 $\mathbf{ŷ}(k)$ を返します。`estim.direct` が `true` の場合、状態推定を修正するためにメソッド [`preparestate!`](@ref) を事前に呼び出す必要があります。

[`StateEstimator`](@ref) オブジェクトを呼び出すと、この `evaloutput` メソッドが呼ばれます。

# 例

```jldoctest
julia> kf = SteadyKalmanFilter(setop!(LinModel(tf(2, [10, 1]), 5), yop=[20]), direct=false);

julia> ŷ = evaloutput(kf)
1-element Vector{Float64}:
 20.0
```
