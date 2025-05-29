```
evaloutput(estim::StateEstimator, d=[]) -> ŷ
```

`StateEstimator`は、`estim.x̂0`の状態と摂動`d`から`ŷ`を出力します。

現在の時間ステップでの`estim`の出力$\mathbf{ŷ}(k)$を返します。`estim.direct`が`true`の場合、状態推定を修正するために、事前にメソッド[`preparestate!`](@ref)を呼び出す必要があります。

[`StateEstimator`](@ref)オブジェクトを呼び出すと、この`evaloutput`メソッドが呼び出されます。

# 例

```jldoctest
julia> kf = SteadyKalmanFilter(setop!(LinModel(tf(2, [10, 1]), 5), yop=[20]), direct=false);

julia> ŷ = evaloutput(kf)
1-element Vector{Float64}:
 20.0
```
