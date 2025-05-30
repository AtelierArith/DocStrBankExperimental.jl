```
LinMPC(model::LinModel; <キーワード引数>)
```

[`LinModel`](@ref) `model` に基づいて線形予測制御器を構築します。

制御器は、各離散時間 $k$ において次の目的関数を最小化します：

$$
\begin{aligned}
\min_{\mathbf{Z}, ϵ}    \mathbf{(R̂_y - Ŷ)}' \mathbf{M}_{H_p} \mathbf{(R̂_y - Ŷ)}
                      + \mathbf{(ΔU)}'      \mathbf{N}_{H_c} \mathbf{(ΔU)}        \\
                      + \mathbf{(R̂_u - U)}' \mathbf{L}_{H_p} \mathbf{(R̂_u - U)} 
                      + C ϵ^2
\end{aligned}
$$

[`setconstraint!`](@ref) の制約に従い、重み行列はデフォルトで $H_p$ または $H_c$ 回繰り返されます：

$$
\begin{aligned}
    \mathbf{M}_{H_p} &= \text{diag}\mathbf{(M,M,...,M)}     \\
    \mathbf{N}_{H_c} &= \text{diag}\mathbf{(N,N,...,N)}     \\
    \mathbf{L}_{H_p} &= \text{diag}\mathbf{(L,L,...,L)}     
\end{aligned}
$$

時間変化する非対角重みもサポートされています。終端重みを指定するには、$\mathbf{M}_{H_p}$ の最後のブロックを修正します。決定ベクトル $\mathbf{Z}$ の内容は、選択した [`TranscriptionMethod`](@ref) に依存します（デフォルトは [`SingleShooting`](@ref) で、したがって $\mathbf{Z = ΔU}$ です）。$\mathbf{ΔU}$ には、入力の増分 $\mathbf{Δu}(k+j) = \mathbf{u}(k+j) - \mathbf{u}(k+j-1)$ が $j=0$ から $H_c-1$ まで含まれ、$\mathbf{Ŷ}$ ベクトル、出力予測 $\mathbf{ŷ}(k+j)$ が $j=1$ から $H_p$ まで、そして $\mathbf{U}$ ベクトル、操作された入力 $\mathbf{u}(k+j)$ が $j=0$ から $H_p-1$ まで含まれます。スラック変数 $ϵ$ は、[`setconstraint!`](@ref) ドキュメントに記載されているように制約を緩和します。詳細な名称については拡張ヘルプを参照してください。

このメソッドは、デフォルトの状態推定器、デフォルト引数を持つ [`SteadyKalmanFilter`](@ref) を使用します。この制御器は、各時間ステップで最適化のためのメモリを割り当てます。

# 引数

  * `model::LinModel` : 制御器の予測と状態推定に使用されるモデル。
  * `Hp=10+nk` : 予測ホライズン $H_p$、`nk` は `model` の遅延の数です。
  * `Hc=2` : 制御ホライズン $H_c$。
  * `Mwt=fill(1.0,model.ny)` : $\mathbf{M}$ 重み行列の主対角線（ベクトル）。
  * `Nwt=fill(0.1,model.nu)` : $\mathbf{N}$ 重み行列の主対角線（ベクトル）。
  * `Lwt=fill(0.0,model.nu)` : $\mathbf{L}$ 重み行列の主対角線（ベクトル）。
  * `M_Hp=Diagonal(repeat(Mwt,Hp))` : 正半定値対称行列 $\mathbf{M}_{H_p}$。
  * `N_Hc=Diagonal(repeat(Nwt,Hc))` : 正半定値対称行列 $\mathbf{N}_{H_c}$。
  * `L_Hp=Diagonal(repeat(Lwt,Hp))` : 正半定値対称行列 $\mathbf{L}_{H_p}$。
  * `Cwt=1e5` : スラック変数の重み $C$（スカラー）、ハード制約のみの場合は `Cwt=Inf` を使用します。
  * `transcription=SingleShooting()` : 最適化のための [`TranscriptionMethod`](@ref)。
  * `optim=JuMP.Model(OSQP.MathOptInterfaceOSQP.Optimizer)` : 予測制御器で使用される二次最適化器、[`JuMP.Model`](@extref) オブジェクトとして提供されます（デフォルトは [`OSQP`](https://osqp.org/docs/parsers/jump.html) 最適化器）。
  * 追加のキーワード引数は [`SteadyKalmanFilter`](@ref) コンストラクタに渡されます。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 4);

julia> mpc = LinMPC(model, Mwt=[0, 1], Nwt=[0.5], Hp=30, Hc=1)
LinMPC controller with a sample time Ts = 4.0 s, OSQP optimizer, SteadyKalmanFilter estimator and:
 30 prediction steps Hp
  1 control steps Hc
  1 slack variable ϵ (control constraints)
  1 manipulated inputs u (0 integrating states)
  4 estimated states x̂
  2 measured outputs ym (2 integrating states)
  0 unmeasured outputs yu
  0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    操作された入力のセットポイント $\mathbf{r_u}$ は一般的ではありませんが、`nu > ny` の場合、過剰駆動システムにとって興味深い場合があります（例：経済的コストが低い解を優先する）。デフォルトの `Lwt` 値は、この機能がデフォルトで無効であることを意味します。

    目的関数は次の名称規則に従います：

    | 変数                 | 説明                            | サイズ              |
    |:------------------ |:----------------------------- |:---------------- |
    | $H_p$              | 予測ホライズン（整数）                   | `()`             |
    | $H_c$              | 制御ホライズン（整数）                   | `()`             |
    | $\mathbf{Z}$       | 決定変数ベクトル（$ϵ$ を除く）             | var.             |
    | $\mathbf{ΔU}$      | $H_c$ にわたる操作された入力の増分          | `(nu*Hc,)`       |
    | $\mathbf{D̂}$      | $H_p$ にわたる予測された測定された外乱        | `(nd*Hp,)`       |
    | $\mathbf{Ŷ}$      | $H_p$ にわたる予測された出力             | `(ny*Hp,)`       |
    | $\mathbf{X̂}$      | $H_p$ にわたる予測された状態             | `(nx̂*Hp,)`      |
    | $\mathbf{U}$       | $H_p$ にわたる操作された入力             | `(nu*Hp,)`       |
    | $\mathbf{R̂_y}$    | $H_p$ にわたる予測された出力セットポイント      | `(ny*Hp,)`       |
    | $\mathbf{R̂_u}$    | $H_p$ にわたる予測された操作された入力セットポイント | `(nu*Hp,)`       |
    | $\mathbf{M}_{H_p}$ | $H_p$ にわたる出力セットポイント追跡重み       | `(ny*Hp, ny*Hp)` |
    | $\mathbf{N}_{H_c}$ | $H_c$ にわたる操作された入力増分重み         | `(nu*Hc, nu*Hc)` |
    | $\mathbf{L}_{H_p}$ | $H_p$ にわたる操作された入力セットポイント追跡重み  | `(nu*Hp, nu*Hp)` |
    | $C$                | スラック変数の重み                     | `()`             |
    | $ϵ$                | 制約の緩和のためのスラック変数               | `()`             |


```
