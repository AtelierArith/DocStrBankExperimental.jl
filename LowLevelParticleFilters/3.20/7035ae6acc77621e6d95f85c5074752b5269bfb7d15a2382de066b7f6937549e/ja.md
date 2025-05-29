```
ExtendedKalmanFilter(kf, dynamics, measurement; Ajac, Cjac)
ExtendedKalmanFilter(dynamics, measurement, R1,R2,d0=MvNormal(Matrix(R1)); nu::Int, p = NullParameters(), α = 1.0, check = true)
```

線形化を使用して不確実性を伝播させる非線形状態推定器です。

拡張カルマンフィルタのコンストラクタは、動力学関数と測定関数を受け取り、共分散行列または[`KalmanFilter`](@ref)のいずれかを受け取ります。前者のコンストラクタが使用される場合、システム動力学への入力の数`nu`はキーワード引数として明示的に提供する必要があります。

デフォルトでは、フィルタは内部的にForwardDiffを使用して動力学を線形化します。ユーザーが提供するヤコビ行列関数は、キーワード引数`Ajac`と`Cjac`として提供できます。これらの関数は、`(x,u,p,t)::AbstractMatrix`というシグネチャを持つ必要があり、`x`は状態、`u`は入力、`p`はパラメータ、`t`は時間です。

動力学関数と測定関数は以下の形式です。

```
x(t+1) = dynamics(x, u, p, t) + w
y      = measurement(x, u, p, t) + e
```

ここで、`w ~ N(0, R1)`、`e ~ N(0, R2)`、および`x(0) ~ d0`です。

行列`R1, R2`は時間変化する可能性があり、例えば、`R1[:, :, t]`は時間インデックス`t`での$R_1$行列を含みます。また、以下の形式の関数として与えることもできます。

```
Rfun(x, u, p, t) -> R
```

これにより、例えば、動力学の摂動$w$が関数への入力引数である場合に、動力学を摂動入力に関して線形化する関数を$R_1$のために作成することができます。このように（動力学が関数シグネチャ`f(x, u, p, t, w)`を持つと仮定して）：

```
function R1fun(x,u,p,t)
    Bw = ForwardDiff.jacobian(w->f(x, u, p, t, w), zeros(length(w)))
    Bw * R1 * Bw'
end
```

関数を提供する際には、状態、入力、出力の次元`nx, nu, ny`を`ExtendedKalmanFilter`コンストラクタにキーワード引数として提供する必要があります。これらは関数シグネチャから推測できないためです。最大のパフォーマンスを得るために、StaticArrays.jlから静的サイズの行列を提供してください。

また、通常`ExtendedKalmanFilter`よりも精度が高い[`UnscentedKalmanFilter`](@ref)も参照してください。カルマンフィルタ`kf`の設定方法についての詳細な手順は[`KalmanFilter`](@ref)を参照してください。
