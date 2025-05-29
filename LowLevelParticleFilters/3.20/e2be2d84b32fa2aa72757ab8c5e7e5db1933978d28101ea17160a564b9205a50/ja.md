```
RBPF{IPD,IPM,AUGD}(N::Int, kf, dynamics, nl_measurement_model::AbstractMeasurementModel, R1n, d0n; An, nu::Int, Ts=1.0, p=NullParameters(), names, rng = Xoshiro(), resample_threshold=0.1)
```

ラオ-ブラックウェル化粒子フィルタ、別名「周辺化粒子フィルタ」。このフィルタは、各粒子が線形サブ構造の推定を担当するカルマンフィルタである粒子フィルタです。

!!! warning "実験的"
    このフィルタは現在実験的と見なされており、ユーザーインターフェースは将来的にセマンティックバージョニングを尊重せずに変更される可能性があります。


このフィルタは、動力学が以下の参考文献の「モデル2」に従うと仮定しています。すなわち、動力学は次のように記述されます。

$$
 \begin{align}
     x_{t+1}^n &= f_n(x_t^n, u, p, t) + A_n(x_t^n, u, p, t) x_t^l + w_t^n, \quad &w_t^n \sim \mathcal{N}(0, R_1^n) \\
     x_{t+1}^l &= A(...) x_t^l + Bu + w_t^l, \quad &w_t^l \sim \mathcal{N}(0, R_1^l) \\
     y_t &= g(x_t^n, u, p, t) + C(...) x_t^l + e_t, \quad &e_t \sim \mathcal{N}(0, R_2)
 \end{align}
$$

ここで、$x^n$は非線形動力学を持つ状態のサブセットであり、$x^l$は状態の線形部分です。全体の状態ベクトルは、ベクトル`[xn; xl]`のように振る舞う特別なタイプ[`RBParticle`](@ref)によって表されますが、`xn, xl`および共分散`R`または`xl`を別々に保存します。

  * `N`: 粒子の数
  * `kf`: 線形部分に使用される内部カルマンフィルタ。これは線形サブスペースの動力学をエンコードします。カルマンフィルタの行列$A, B, C, D, R_1^l$は、行列を返す`x, u, p, t`の関数である可能性があります。そのような関数によって受け取られる状態`x`は、フィールド`xn`と`xl`を持つタイプ[`RBParticle`](@ref)です。
  * `dynamics`: 非線形サブステートの動力学の非線形部分$f_n$、すなわち`f(xn, u, p, t)`
  * `nl_measurement_model`: $g$と測定ノイズ分布$R_2$を保存する[`RBMeasurementModel`](@ref)のインスタンス。
  * `R1n`: 非線形状態動力学のノイズ分布、これは共分散行列または分布である可能性があります。`An = nothing`の場合、これは任意の分布である可能性がありますが、そうでない場合は`MvNormal`または`SimpleMvNormal`のインスタンスでなければなりません。
  * `d0n`: 非線形状態$x_0^n$の初期分布。
  * `An`: 非線形状態に対する線形効果を記述する行列、すなわち$A_n x^l$。これは行列または行列を返す`x, u, p, t`の関数である可能性があります。非線形状態に対する線形効果がない場合は`An = nothing`を渡します。そのような関数によって受け取られる`x`は、フィールド`xn`と`xl`を持つタイプ[`RBParticle`](@ref)です。
  * `nu`: 制御入力の数
  * `Ts`: サンプリング時間
  * `p`: パラメータ
  * `names`: 信号名、[`SignalNames`](@ref)のインスタンス
  * `rng`: 擬似乱数生成器
  * `resample_threshold`: 再サンプリングの閾値

記事["Marginalized Particle Filters for Mixed Linear/Nonlinear State-space Models" by Thomas Schön, Fredrik Gustafsson, and Per-Johan Nordlund](https://people.isy.liu.se/rt/schon/Publications/SchonGN2004.pdf)に基づいています。

## 拡張ヘルプ

この論文には、線形部分が非線形状態によって線形に影響を受けるより一般的なモデルが含まれています。また、可能な簡略化が生じる特別なケースについても詳述しています。

  * `C == 0`かつ`D == 0`の場合、測定はカルマンフィルタによって使用されず、測定ノイズに対して任意の確率分布を持つことができます。
  * `An == 0`の場合、非線形状態は線形状態に影響されず、非線形状態ノイズ`R1n`に対して任意の確率分布を持つことができます。そうでない場合、`R1n`はガウス分布でなければなりません。
