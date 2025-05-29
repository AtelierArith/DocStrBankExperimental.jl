```
add_thermal_noise(sim::AbstractSim, Temp::NumberOrArrayOrFunction; name="thermal", scaling=t -> 1.0, k_B=k_B)
```

シミュレーションに熱雑音フィールドを追加します。マイクロ磁気モデルでは、熱雑音は次のように定義されます。

$$
\mathbf{b}^u = \eta \sqrt \frac{2 \alpha k_B T}{\mu_0 M_s \gamma \Delta V dt}
$$

ここで、$\eta$は正規分布に従うランダム数であり、$\gamma=2.211\times 10^5$ m/(A·s)はジャイロ磁気比です。

原子モデルでは、熱雑音は次のように定義されます。

$$
\mathbf{b}^u = \eta \sqrt \frac{2 \alpha k_B T}{\gamma \mu_s dt}.
$$

ここで、$\eta$は正規分布に従うランダム数であり、$\gamma=1.76\times 10^{11}$ rad/(T·s)です。

### 引数

  * `sim::AbstractSim`: シミュレーションオブジェクト。
  * `Temp::NumberOrArrayOrFunction`: 温度値（定数、配列、または関数である可能性があります）。
  * `name::String`: 雑音フィールドの名前（デフォルト: `"thermal"`）。
  * `scaling::Function`: 時間にわたって雑音をスケーリングする関数（デフォルト: `t -> 1.0`）。
  * `k_B::Float64`: ボルツマン定数（デフォルト: `k_B`）。

### 例

```julia
# 定温100 Kでスケーリング関数を持つ熱雑音を追加
add_thermal_noise(sim, 100.0, scaling = t -> exp(-t/1e-9))
```
