```
SteadyKalmanFilter(model::LinModel; <キーワード引数>)
```

[`LinModel`](@ref) `model`を用いて定常状態カルマンフィルタを構築します。

定常状態（または[漸近的](https://en.wikipedia.org/wiki/Kalman_filter#Asymptotic_form)）カルマンフィルタは、プロセスモデルに基づいています：

$$
\begin{aligned}
    \mathbf{x}(k+1) &= 
            \mathbf{Â x}(k) + \mathbf{B̂_u u}(k) + \mathbf{B̂_d d}(k) + \mathbf{w}(k) \\
    \mathbf{y^m}(k) &= \mathbf{Ĉ^m x}(k) + \mathbf{D̂_d^m d}(k) + \mathbf{v}(k) \\
    \mathbf{y^u}(k) &= \mathbf{Ĉ^u x}(k) + \mathbf{D̂_d^u d}(k)
\end{aligned}
$$

センサーのノイズ $\mathbf{v}(k)$ とプロセスのノイズ $\mathbf{w}(k)$ は、相関のないゼロ平均のホワイトノイズベクトルであり、それぞれの共分散は $\mathbf{R̂}$ と $\mathbf{Q̂}$ です。引数は標準偏差 σ であり、出力と状態と同じ単位です。行列 $\mathbf{Â, B̂_u, B̂_d, Ĉ, D̂_d}$ は、確率モデルで拡張された `model` 行列であり、これは積分器の数 `nint_u` と `nint_ym` によって指定されます（詳細は拡張ヘルプを参照）。同様に、共分散行列は $\mathbf{Q̂ = \text{diag}(Q,  Q_{int_u}, Q_{int_{ym}})}$ と $\mathbf{R̂ = R}$ で拡張されます。拡張ヘルプでは、共分散の調整に関するガイドラインが提供されています。行列 $\mathbf{Ĉ^m, D̂_d^m}$ は、測定された出力 $\mathbf{y^m}$ に対応する $\mathbf{Ĉ, D̂_d}$ の行です（未測定のものについては、$\mathbf{Ĉ^u, D̂_d^u}$）。カルマンフィルタは、`direct` が `true` の場合、最新の測定値 $\mathbf{x̂}_k(k)$ で現在の状態を推定します。そうでない場合は、次の時間ステップの状態 $\mathbf{x̂}_k(k+1)$ を予測します。この推定器は、割り当てなしで使用できます。

# 引数

!!! info
    *`強調`* されたキーワード引数は、非Unicodeの代替です。


  * `model::LinModel` : （決定論的）推定のためのモデル。
  * `i_ym=1:model.ny` : 測定された出力 $\mathbf{y^m}$ の `model` 出力インデックス、残りは未測定の $\mathbf{y^u}$ です。
  * `σQ=fill(1/model.nx,model.nx)` または *`sigmaQ`* : `model` のプロセスノイズ共分散 $\mathbf{Q}$ の主対角線を、標準偏差ベクトルとして指定します。
  * `σR=fill(1,length(i_ym))` または *`sigmaR`* : `model` 測定出力のセンサーノイズ共分散 $\mathbf{R}$ の主対角線を、標準偏差ベクトルとして指定します。
  * `nint_u=0`: 操作入力の未測定の擾乱に対する確率モデルのための積分器の数（ベクトル）、積分器なしの場合は `nint_u=0` を使用します（詳細は拡張ヘルプを参照）。
  * `nint_ym=default_nint(model,i_ym,nint_u)` : 測定出力の未測定の擾乱に対する `nint_u` と同様ですが、積分器なしの場合は `nint_ym=0` を使用します（詳細は拡張ヘルプを参照）。
  * `σQint_u=fill(1,sum(nint_u))` または *`sigmaQint_u`* : 操作入力の未測定の擾乱に対する $\mathbf{Q_{int_u}}$ のための `σQ` と同様です（積分器で構成されています）。
  * `σQint_ym=fill(1,sum(nint_ym))` または *`sigmaQint_u`* : 測定出力の未測定の擾乱に対する $\mathbf{Q_{int_{ym}}}$ のための `σQ` と同様です（積分器で構成されています）。
  * `direct=true`: $\mathbf{y^m}$ からの直接伝送で構築します（現在の推定器、遅延/予測形式とは対照的）。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5);

julia> estim = SteadyKalmanFilter(model, i_ym=[2], σR=[1], σQint_ym=[0.01])
SteadyKalmanFilter estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u (0 integrating states)
 3 estimated states x̂
 1 measured outputs ym (1 integrating states)
 1 unmeasured outputs yu
 0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    `σR` 引数は、一般的にセンサーノイズの推定標準偏差に固定されています。`σQ`、`σQint_u` および `σQint_ym` 引数は、フィルタ応答を調整するために使用できます。これらを増加させると、フィルタは擾乱に対してより応答的になりますが、測定ノイズに対してより敏感になります。

    `nint_u` ベクトルによるモデルの拡張は、モデルの操作入力に積分器を追加し、`nint_ym` は測定出力に追加します。これにより、推定器が状態フィードバックとしてコントローラで使用されるときに、積分動作が作成されます。デフォルトでは、メソッド [`default_nint`](@ref) は、可能であれば測定出力ごとに1つの積分器を追加します。引数 `nint_ym` は、各測定出力に対して以下のルールに従って調整することもできます：

      * モデル出力がすでに積分している場合は、0の積分器を使用します（そうでないと観測不可能になります）
      * 出力の擾乱が通常「ステップ状」の場合は、1の積分器を使用します
      * 出力の擾乱が通常「ランプ状」の場合は、2の積分器を使用します

    関数 [`init_estimstoch`](@ref) は、推定のための確率モデルを構築します。

    !!! tip
        `σQint_u` および `σQint_ym` の値を増加させると、積分動作の「ゲイン」が増加します。


    コンストラクタは、[`kalman`](@extref ControlSystemsBase.kalman) 関数を使用して定常状態カルマンゲイン `K̂` を事前に計算します。これは、`model` 行列が条件不良である場合など、失敗することがあります。その場合は、代替の時間変化型 [`KalmanFilter`](@ref) を試すことができます。


```
