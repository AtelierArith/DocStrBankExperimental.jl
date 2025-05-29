```
IteratedExtendedKalmanFilter(kf, dynamics, measurement; Ajac, Cjac, step, maxiters, epsilon)
IteratedExtendedKalmanFilter(dynamics, measurement, R1,R2,d0=SimpleMvNormal(Matrix(R1)); nu::Int, ny=size(R2,1), Cjac = nothing, step = 1.0, maxiters=10, epsilon=1e-8)
```

非線形状態推定器が線形化を使用して不確実性を伝播させます。`ExtendedKalmanFilter`オブジェクトを返しますが、ガウス-ニュートンに基づく測定補正ステップを反復します。

拡張カルマンフィルタの反復バージョンのコンストラクタは、動力学と測定関数を受け取り、共分散行列または[`KalmanFilter`](@ref)のいずれかを受け取ります。前者のコンストラクタが使用される場合、システム動力学への入力の数`nu`はキーワード引数として明示的に提供する必要があります。

デフォルトでは、フィルタは内部的にForwardDiffを使用して動力学を線形化します。ユーザー提供のヤコビアン関数は、キーワード引数`Ajac`および`Cjac`として提供できます。これらの関数は、`(x,u,p,t)::AbstractMatrix`というシグネチャを持つ必要があります。ここで、`x`は状態、`u`は入力、`p`はパラメータ、`t`は時間です。

動力学と測定関数は次の形式です。

```
x(t+1) = dynamics(x, u, p, t) + w
y      = measurement(x, u, p, t) + e
```

ここで、`w ~ N(0, R1)`、`e ~ N(0, R2)`、および`x(0) ~ d0`です。

  * `step`はガウス-ニュートン反復のステップサイズです。0と1の間の浮動小数点数です。デフォルトは1.0で、ほとんどのアプリケーションには十分です。より困難なアプリケーションでは、より小さなステップサイズが必要になる場合があります。
  * `maxiters`は最大反復回数です。デフォルトは10です。通常は少数の反復が必要です。より多くの反復が必要な場合は、UKFの使用を検討してください。
  * `epsilon`は収束基準です。デフォルトは1e-8です。

より堅牢な[`UnscentedKalmanFilter`](@ref)も参照してください。カルマンフィルタ`kf`のセットアップ方法についての詳細な指示は[`KalmanFilter`](@ref)を参照してください。
