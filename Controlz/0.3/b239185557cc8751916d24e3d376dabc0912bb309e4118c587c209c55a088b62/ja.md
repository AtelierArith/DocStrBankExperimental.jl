```
pidc = PIDController(Kc, τI, τD, α=0.0)
```

比例-積分-微分（PID）コントローラを構築するには、コントローラゲイン、積分時間定数、微分時間定数、および次の伝達関数表現で定義された微分フィルタを指定します：

$$
g_c(s)=K_c \left[1+\frac{1}{\tau_I s}+\tau_D s \frac{1}{\alpha \tau_D s + 1}\right]
$$

# 引数

  * `Kc::Float64`: コントローラゲイン
  * `τI::Float64`: 積分時間定数
  * `τD::Float64`: 微分時間定数
  * `α::Float64`: 微分フィルタ

# 例

```julia
pidc = PIDController(1.0, 3.0, 0.1) # PIDコントローラのパラメータを指定
gc = TransferFunction(pidc) # これらのPIDコントローラパラメータで伝達関数を構築
```
