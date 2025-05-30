```
DiscretePID(; K = 1, Ti = false, Td = false, Tt = √(Ti*Td), N = 10, b = 1, umin = -Inf, umax = Inf, Ts, I = 0, D = 0, yold = 0)
```

セットポイント加重と積分アンチワインドアップを持つ離散時間PIDコントローラ。コントローラは標準形式で実装されています。

$$
u = K \left( e + \dfrac{1}{Ti} \int e dt + T_d \dfrac{de}{dt} \right)
$$

$$
U(s) = K \left( bR(s) - Y(s) + \dfrac{1}{sT_i} \left( R(s) Y(s) \right) - \dfrac{sT_d}{1 + s T_d / N}Y(s)
$$

コントローラを次のように呼び出します。

```julia
u = pid(r, y, uff) # uffはオプション
u = calculate_control!(pid, r, y, uff) # 上記と同等
```

# 引数:

  * `K`: 比例ゲイン
  * `Ti`: 積分時間
  * `Td`: 微分時間
  * `Tt`: アンチワインドアップ用のリセット時間
  * `N`: 最大微分ゲイン
  * `b`: 比例項におけるセットポイントの割合
  * `umin`: 出力の下限
  * `umax`: 出力の上限
  * `Ts`: サンプリング周期
  * `I`: 積分部分
  * `D`: 微分部分
  * `yold`: 最後の測定信号

さらに[`calculate_control!`](@ref)、[`set_K!`](@ref)、[`set_Ti!`](@ref)、[`set_Td!`](@ref)、[`reset_state!`](@ref)を参照してください。
