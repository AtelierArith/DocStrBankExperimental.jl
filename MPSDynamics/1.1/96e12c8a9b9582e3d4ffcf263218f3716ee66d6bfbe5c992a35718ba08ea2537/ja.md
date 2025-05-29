```
protontransfermpo(ω0e,ω0k,x0e,x0k, Δ, dRC, d, N, chainparams, RCparams, λreorg)
```

反応座標 (RC) テンソルで記述されたシステムのための MPO を生成します。二準位システムと反応座標テンソルのハミルトニアンは次のように表されます。

$$
H_S + H_{RC} + H_{int}^{S-RC} = \omega^0_{e} |e\rangle \langle e| + \omega^0_{k} |k\rangle \langle k| + \Delta (|e\rangle \langle k| + |k\rangle \langle e|) + \omega_{RC} (d^{\dagger}d + \frac{1}{2}) + g_{e} |e\rangle \langle e|( d + d^{\dagger})+ g_{k} |k \rangle \langle k|( d + d^{\dagger})
$$

RC テンソルはボソニックバスに結合されており、誘導された再編成エネルギーを考慮しています。$H_B + H_{int}^{RC-B} = \int_{-∞}^{+∞} dk ω_k b_k^\dagger b_k - (d + d^{\dagger})\int_0^∞ dω\sqrt{J(ω)}(b_ω^\dagger+b_ω) + \lambda_{reorg}(d + d^{\dagger})^2$ ここで、$\lambda_{reorg} = \int \frac{J(\omega)}{\omega}d\omega.$

# 引数

  * `ω0e`: 反応座標値 x=0 におけるエノールエネルギー
  * `ω0k`: 反応座標値 x=0 におけるケトエネルギー
  * `x0e`: エノール平衡変位
  * `x0k`: ケト平衡変位
  * `Δ`: エノールとケトの間の直接結合
  * `dRC`: RC テンソルのフォック空間
  * `d`: チェーンモードのフォック状態の数
  * `N`: ボソニックチェーンの長さ
  * `chainparams`: チェーンパラメータ、形式は `chainparams`=$[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$ であり、任意の温度で任意のスペクトル密度 $J(ω)$ を表すように選択できます。
  * `RCparams`: RC テンソルパラメータ、形式は `RCparams`=$[ω_RC,-g/x]$
  * `λreorg`: 再編成エネルギー
