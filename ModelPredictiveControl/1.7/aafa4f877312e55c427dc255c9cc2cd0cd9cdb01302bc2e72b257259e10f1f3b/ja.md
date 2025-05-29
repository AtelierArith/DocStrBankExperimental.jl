```
setconstraint!(mpc::PredictiveController; <keyword arguments>) -> mpc
```

[`PredictiveController`](@ref) `mpc`の境界制約パラメータを設定します。

予測制御器は、次のように定義されたソフト制約とハード制約の両方をサポートします：

$$
\begin{alignat*}{3}
    \mathbf{u_{min}  - c_{u_{min}}}  ϵ ≤&&\       \mathbf{u}(k+j) &≤ \mathbf{u_{max}  + c_{u_{max}}}  ϵ &&\qquad  j = 0, 1 ,..., H_p - 1 \\
    \mathbf{Δu_{min} - c_{Δu_{min}}} ϵ ≤&&\      \mathbf{Δu}(k+j) &≤ \mathbf{Δu_{max} + c_{Δu_{max}}} ϵ &&\qquad  j = 0, 1 ,..., H_c - 1 \\
    \mathbf{y_{min}  - c_{y_{min}}}  ϵ ≤&&\       \mathbf{ŷ}(k+j) &≤ \mathbf{y_{max}  + c_{y_{max}}}  ϵ &&\qquad  j = 1, 2 ,..., H_p     \\
    \mathbf{x̂_{min}  - c_{x̂_{min}}}  ϵ ≤&&\     \mathbf{x̂}_i(k+j) &≤ \mathbf{x̂_{max}  + c_{x̂_{max}}}  ϵ &&\qquad  j = H_p
\end{alignat*}
$$

また、$ϵ ≥ 0$です。最後の行は、ホライズンの終わりにおける状態に適用される端末制約です（詳細は拡張ヘルプを参照）。境界とソフトネスパラメータ$\mathbf{c}$に関する詳細は[`MovingHorizonEstimator`](@ref)の制約を参照してください。出力および端末制約はデフォルトで全てソフトです。時間変化する制約については拡張ヘルプを参照してください。

# 引数

!!! info
    キーワード引数 `Δumin`, `Δumax`, `c_Δumin`, `c_Δumax`, `x̂min`, `x̂max`, `c_x̂min`, `c_x̂max` およびそれらの大文字バージョンには、非Unicodeの代替があります。例えば、*`Deltaumin`*, *`xhatmax`* および *`C_Deltaumin`*。

    デフォルトの制約は明確にするためにここに記載されていますが、キーワード引数を省略してもデフォルト値に再割り当てされることはありません（デフォルトは構築時にのみ設定されます）。


  * `mpc::PredictiveController` : 制約を設定する予測制御器
  * `umin=fill(-Inf,nu)` / `umax=fill(+Inf,nu)` : 操作入力の境界 $\mathbf{u_{min/max}}$
  * `Δumin=fill(-Inf,nu)` / `Δumax=fill(+Inf,nu)` : 操作入力の増分境界 $\mathbf{Δu_{min/max}}$
  * `ymin=fill(-Inf,ny)` / `ymax=fill(+Inf,ny)` : 予測出力の境界 $\mathbf{y_{min/max}}$
  * `x̂min=fill(-Inf,nx̂)` / `x̂max=fill(+Inf,nx̂)` : 端末制約の境界 $\mathbf{x̂_{min/max}}$
  * `c_umin=fill(0.0,nu)` / `c_umax=fill(0.0,nu)` : `umin` / `umax` のソフトネス重み $\mathbf{c_{u_{min/max}}}$
  * `c_Δumin=fill(0.0,nu)` / `c_Δumax=fill(0.0,nu)` : `Δumin` / `Δumax` のソフトネス重み $\mathbf{c_{Δu_{min/max}}}$
  * `c_ymin=fill(1.0,ny)` / `c_ymax=fill(1.0,ny)` : `ymin` / `ymax` のソフトネス重み $\mathbf{c_{y_{min/max}}}$
  * `c_x̂min=fill(1.0,nx̂)` / `c_x̂max=fill(1.0,nx̂)` : `x̂min` / `x̂max` のソフトネス重み $\mathbf{c_{x̂_{min/max}}}$
  * 上記のすべてのキーワード引数の最初の文字を大文字にしたもの（端末制約を除く）、例：`Ymax` または `C_Δumin`：時間変化する制約用（拡張ヘルプを参照）

# 例

```jldoctest
julia> mpc = LinMPC(setop!(LinModel(tf(3, [30, 1]), 4), uop=[50], yop=[25]));

julia> mpc = setconstraint!(mpc, umin=[0], umax=[100], Δumin=[-10], Δumax=[+10])
LinMPCコントローラ、サンプル時間 Ts = 4.0 s、OSQPオプティマイザ、SteadyKalmanFilter推定器、及び：
  10予測ステップ Hp
  2制御ステップ Hc
  1スラック変数 ϵ（制御制約）
  1操作入力 u（0統合状態）
  2推定状態 x̂
  1測定出力 ym（1統合状態）
  0未測定出力 yu
  0測定外乱 d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    端末制約は、名目プラントモデルに対する閉ループ安定性保証を提供します。ただし、実際には実現不可能な問題を引き起こす可能性があります。実際には、端末制約なしで十分に大きな予測ホライズン $H_p$ があれば、通常は安定性に十分です。`mpc.estim.direct==true` の場合、推定器は $i = k$（現在の時間ステップ）で状態を計算します。そうでない場合は $i = k - 1$ で計算します。端末制約は拡張状態ベクトル $\mathbf{x̂}$ に適用されることに注意してください（詳細は[`SteadyKalmanFilter`](@ref)の拡張を参照）。

    変数制約については、[`moveinput!`](@ref)を呼び出した後、すなわち実行時に境界を変更できますが、ソフトネスパラメータ $\mathbf{c}$ は変更できません。実行時に `±Inf` の境界を変更することはできません。

    !!! tip
        変数を制約なしに保ちながら、実行時に後で制約を追加できるようにするには、コントローラを作成する際に境界を十分に大きな絶対値に設定します（ただし `±Inf` とは異なる値に）。


    また、$H_p$ および $H_c$ ホライズンにわたる時間変化する制約を指定することも可能です。この場合、次のように定義されます：

    $$
    \begin{alignat*}{3}
        \mathbf{U_{min}  - C_{u_{min}}}  ϵ ≤&&\ \mathbf{U}  &≤ \mathbf{U_{max}  + C_{u_{max}}}  ϵ \\
        \mathbf{ΔU_{min} - C_{Δu_{min}}} ϵ ≤&&\ \mathbf{ΔU} &≤ \mathbf{ΔU_{max} + C_{Δu_{max}}} ϵ \\
        \mathbf{Y_{min}  - C_{y_{min}}}  ϵ ≤&&\ \mathbf{Ŷ}  &≤ \mathbf{Y_{max}  + C_{y_{max}}}  ϵ
    \end{alignat*}
    $$

    このためには、上記と同じキーワード引数を使用しますが、最初の文字を大文字にします：

      * `Umin`  / `Umax`  / `C_umin`  / `C_umax`  : $\mathbf{U}$ 制約 `(nu*Hp,)`。
      * `ΔUmin` / `ΔUmax` / `C_Δumin` / `C_Δumax` : $\mathbf{ΔU}$ 制約 `(nu*Hc,)`。
      * `Ymin`  / `Ymax`  / `C_ymin`  / `C_ymax`  : $\mathbf{Ŷ}$ 制約 `(ny*Hp,)`。


```
