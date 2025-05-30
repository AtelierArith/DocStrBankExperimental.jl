```
sim!(
    estim::StateEstimator,
    N::Int,
    u = estim.model.uop .+ 1,
    d = estim.model.dop;
    <keyword arguments>
) -> res
```

`estim` 推定器の閉ループシミュレーションを `N` ステップで実行し、デフォルトで入力バンプを使用します。

利用可能なオプションについては、引数を参照してください。ノイズは標準偏差 σ ベクトルとして提供されます。`plant` のシミュレーションされたセンサーおよびプロセスノイズは、それぞれ `y_noise` および `x_noise` 引数によって指定されます。

# 引数

!!! info
    *`emphasis`* で強調されたキーワード引数は、非Unicodeの代替です。


  * `estim::StateEstimator` : シミュレーションする状態推定器
  * `N::Int` : 時間ステップでのシミュレーションの長さ
  * `u = estim.model.uop .+ 1` : 操作された入力 $\mathbf{u}$ の値
  * `d = estim.model.dop` : 植物の測定された外乱 $\mathbf{d}$ の値
  * `plant::SimModel = estim.model` : シミュレーションされた植物モデル
  * `u_step  = zeros(plant.nu)` : 植物入力 $\mathbf{u}$ に対するステップ負荷外乱
  * `u_noise = zeros(plant.nu)` : 植物入力 $\mathbf{u}$ に対するガウス負荷外乱
  * `y_step  = zeros(plant.ny)` : 植物出力 $\mathbf{y}$ に対するステップ外乱
  * `y_noise = zeros(plant.ny)` : 植物出力 $\mathbf{y}$ に対する加法的ガウスノイズ
  * `d_step  = zeros(plant.nd)` : 測定された外乱 $\mathbf{d}$ に対するステップ
  * `d_noise = zeros(plant.nd)` : 測定された外乱 $\mathbf{d}$ に対する加法的ガウスノイズ
  * `x_noise = zeros(plant.nx)` : 植物状態 $\mathbf{x}$ に対する加法的ガウスノイズ
  * `x_0 = plant.xop` : 植物の初期状態 $\mathbf{x}(0)$
  * `x̂_0 = nothing` または *`xhat_0`* : 初期推定値 $\mathbf{x̂}(0)$、`nothing` の場合は [`initstate!`](@ref) が使用されます
  * `lastu = plant.uop` : $\mathbf{x̂}$ 初期化のための最後の植物入力 $\mathbf{u}$

# 例

```jldoctest
julia> model = LinModel(tf(3, [30, 1]), 0.5);

julia> estim = KalmanFilter(model, σR=[0.5], σQ=[0.25], σQint_ym=[0.01], σPint_ym_0=[0.1]);

julia> res = sim!(estim, 50, [0], y_noise=[0.5], x_noise=[0.25], x_0=[-10], x̂_0=[0, 0])
シミュレーション結果：50 時間ステップの KalmanFilter。
```
