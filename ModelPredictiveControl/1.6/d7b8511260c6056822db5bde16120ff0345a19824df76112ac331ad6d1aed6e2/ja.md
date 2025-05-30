```
setconstraint!(estim::MovingHorizonEstimator; <keyword arguments>) -> estim
```

[`MovingHorizonEstimator`](@ref) `estim`の境界制約パラメータを設定します。

推定された状態 $\mathbf{x̂}$、プロセスノイズ $\mathbf{ŵ}$、およびセンサーノイズ $\mathbf{v̂}$ に対して、ソフト制約とハード制約の両方をサポートしています：

$$
\begin{alignat*}{3}
    \mathbf{x̂_{min} - c_{x̂_{min}}} ϵ ≤&&\   \mathbf{x̂}_k(k-j+p) &≤ \mathbf{x̂_{max} + c_{x̂_{max}}} ϵ &&\qquad  j = N_k, N_k - 1, ... , 0    \\
    \mathbf{ŵ_{min} - c_{ŵ_{min}}} ϵ ≤&&\     \mathbf{ŵ}(k-j+p) &≤ \mathbf{ŵ_{max} + c_{ŵ_{max}}} ϵ &&\qquad  j = N_k, N_k - 1, ... , 1    \\
    \mathbf{v̂_{min} - c_{v̂_{min}}} ϵ ≤&&\     \mathbf{v̂}(k-j+1) &≤ \mathbf{v̂_{max} + c_{v̂_{max}}} ϵ &&\qquad  j = N_k, N_k - 1, ... , 1
\end{alignat*}
$$

また、$ϵ ≥ 0$ です。すべての制約パラメータはベクトルです。境界がない場合は `±Inf` 値を使用します。制約の柔軟性パラメータ $\mathbf{c}$ は、関連する境界の柔軟性を指定する非負の値です。ハード制約には `0.0` 値を使用します（すべてのデフォルト）。推定されたセンサーノイズを制約することは、イノベーション項を制約することと同等であることに注意してください。なぜなら、 $\mathbf{v̂}(k) = \mathbf{y^m}(k) - \mathbf{ŷ^m}(k)$ だからです。定数 $p$、モデルの拡張、および時間変動制約に関する詳細は、拡張ヘルプを参照してください。

# 引数

!!! info
    すべてのキーワード引数には非Unicodeの代替があります。例えば、*`xhatmin`* や *`Vhatmax`* です。

    デフォルトの制約は明確にするためにここに記載されていますが、キーワード引数を省略してもデフォルト値に再割り当てされることはありません（デフォルトは構築時にのみ設定されます）。


  * `estim::MovingHorizonEstimator` : 制約を設定する移動ホライズン推定器
  * `x̂min=fill(-Inf,nx̂)` / `x̂max=fill(+Inf,nx̂)` : 推定された状態の境界 $\mathbf{x̂_{min/max}}$
  * `ŵmin=fill(-Inf,nx̂)` / `ŵmax=fill(+Inf,nx̂)` : 推定されたプロセスノイズの境界 $\mathbf{ŵ_{min/max}}$
  * `v̂min=fill(-Inf,nym)` / `v̂max=fill(+Inf,nym)` : 推定されたセンサーノイズの境界 $\mathbf{v̂_{min/max}}$
  * `c_x̂min=fill(0.0,nx̂)` / `c_x̂max=fill(0.0,nx̂)` : `x̂min` / `x̂max` の柔軟性重み $\mathbf{c_{x̂_{min/max}}}$
  * `c_ŵmin=fill(0.0,nx̂)` / `c_ŵmax=fill(0.0,nx̂)` : `ŵmin` / `ŵmax` の柔軟性重み $\mathbf{c_{ŵ_{min/max}}}$
  * `c_v̂min=fill(0.0,nym)` / `c_v̂max=fill(0.0,nym)` : `v̂min` / `v̂max` の柔軟性重み $\mathbf{c_{v̂_{min/max}}}$
  * 上記のすべてのキーワード引数の最初の文字を大文字にしたもの、例えば `X̂max` や `C_ŵmax` : 時間変動制約用（拡張ヘルプを参照）

# 例

```jldoctest
julia> estim = MovingHorizonEstimator(LinModel(ss(0.5,1,1,0,1)), He=3);

julia> estim = setconstraint!(estim, x̂min=[-50, -50], x̂max=[50, 50])
MovingHorizonEstimator estimator with a sample time Ts = 1.0 s, OSQP optimizer, LinModel and:
 3 estimation steps He
 0 slack variable ϵ (estimation constraints)
 1 manipulated inputs u (0 integrating states)
 2 estimated states x̂
 1 measured outputs ym (1 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    定数 $p=0$ は `estim.direct==true` の場合（現在の形式）、それ以外の場合は $p=1$（予測形式）です。状態 $\mathbf{x̂}$ とプロセスノイズ $\mathbf{ŵ}$ の制約は、[`SteadyKalmanFilter`](@ref) 拡張ヘルプで詳述されている拡張モデルに適用されます。変数制約の場合、境界は [`updatestate!`](@ref) を呼び出した後、すなわち実行時に変更できます。ただし、`±Inf` の境界は除きます。推定ホライズン $H_e$ にわたる時間変動制約も可能であり、数学的には次のように定義されます：

    $$
    \begin{alignat*}{3}
        \mathbf{X̂_{min} - C_{x̂_{min}}} ϵ ≤&&\ \mathbf{X̂} &≤ \mathbf{X̂_{max} + C_{x̂_{max}}} ϵ \\
        \mathbf{Ŵ_{min} - C_{ŵ_{min}}} ϵ ≤&&\ \mathbf{Ŵ} &≤ \mathbf{Ŵ_{max} + C_{ŵ_{max}}} ϵ \\
        \mathbf{V̂_{min} - C_{v̂_{min}}} ϵ ≤&&\ \mathbf{V̂} &≤ \mathbf{V̂_{max} + C_{v̂_{max}}} ϵ
    \end{alignat*}
    $$

    これには、上記と同じキーワード引数を使用しますが、最初の文字を大文字にします：

      * `X̂min` / `X̂max` / `C_x̂min` / `C_x̂max` : $\mathbf{X̂}$ の制約 `(nx̂*(He+1),)`。
      * `Ŵmin` / `Ŵmax` / `C_ŵmin` / `C_ŵmax` : $\mathbf{Ŵ}$ の制約 `(nx̂*He,)`。
      * `V̂min` / `V̂max` / `C_v̂min` / `C_v̂max` : $\mathbf{V̂}$ の制約 `(nym*He,)`。


```
