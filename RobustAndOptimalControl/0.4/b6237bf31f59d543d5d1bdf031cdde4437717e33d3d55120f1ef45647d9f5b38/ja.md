```
diskmargin(L, σ = 0)
diskmargin(L, σ::Real, ω)
```

LTIシステム`L`のディスクマージンを計算します。`L`はループ伝達関数である必要があり、すなわち正方行列である必要があります。`L = PC`の場合、出力摂動のためのディスクマージンが計算され、`L = CP`の場合、入力摂動が考慮されます。メソッド`diskmargin(P, C, args...)`が使用される場合、両方が計算されます。注意点として、`L`がMIMOの場合、同時マージンが計算されます。MIMOシステムの単一ループマージンについては[`loop_diskmargin`](@ref)を参照してください。

実装と表記は["An Introduction to Disk Margins", Peter Seiler, Andrew Packard, and Pascal Gahinet](https://arxiv.org/abs/2003.04771)に従っています。

マージンは返されるオブジェクトのフィールドとして利用可能です。[`Diskmargin`](@ref)を参照してください。

# 引数:

  * `L`: ループ伝達関数。
  * `σ`: ゲイン変動の分布についてあまり知られていない場合、σ = 0は合理的な選択です。これは、同じ相対量でゲインを増加または減少させることを許可します。*ゲインが増加するよりも大きな要因で減少できる場合、σ < 0*の選択が正当化されます。同様に、*ゲインが減少するよりも大きな要因で増加できる場合、σ > 0*の選択が正当化されます。*σ = −1*の場合、ディスクマージン条件はαmax = inv(MT)です。このマージンは、P (1 + δ)の形の乗法的不確実性を持つモデルのロバスト安定性条件に関連しています。*σ = +1*の場合、ディスクマージン条件はαmax = inv(MS)です。
  * `kwargs`: [`hinfnorm`](@ref)計算に送信されます。
  * `ω`: 周波数のベクトルが提供される場合、周波数依存のディスクマージンが計算されます。以下の例を参照してください。

# 例:

```
L = tf(25, [1,10,10,10])
dm = diskmargin(L, 0)
plot(dm) # 最大許容同時ゲインおよび位相変動を示すためにディスクマージンをプロットします。

nyquistplot(L)
plot!(dm, nyquist=true) # ニクイスト除外ディスクをプロットします。ニクイスト曲線は`dm.ω0`でこのディスクに接します。
nyquistplot!(dm.f0*L) # 最悪の摂動`f0`でシステムを摂動させると、曲線は臨界点-1を通過します。

## 周波数依存のマージン
w = exp10.(LinRange(-2, 2, 500))
dms = diskmargin(L, 0, w)
plot(dms; lower=true, phase=true)
```

# 例: MsおよびMtとの関係

```
Ms, wMs = hinfnorm(input_sensitivity(P, C)) # 入力Ms
dm = diskmargin(C*P, 1) # 入力ディスクマージン、スキュー = +1
isapprox(Ms/(Ms-1), dm.gainmargin[2], rtol=1e-2) # Msに基づく保証されたゲインマージン
isapprox(inv(Ms), dm.margin, rtol=1e-2)
isapprox(dm.ω0, wMs, rtol=1e-1)


Mt, wMt = hinfnorm(input_comp_sensitivity(P, C)) # 入力Mt
dm = diskmargin(C*P, -1) # 入力ディスクマージン、スキュー = -1
isapprox(inv(Mt), dm.margin, rtol=1e-2)
isapprox(dm.ω0, wMt, rtol=1e-1)
```

[`ncfmargin`](@ref)および[`loop_diskmargin`](@ref)も参照してください。
