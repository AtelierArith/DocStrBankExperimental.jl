```
pic = PIController(Kc, τI)
```

比例-積分 (PI) コントローラを構築するには、次の伝達関数表現で定義されたコントローラゲインと積分時間定数を指定します：

$$
g_c(s)=K_c \left[1+\frac{1}{\tau_I s}\right]
$$

# 引数

  * `Kc::Float64`: コントローラゲイン
  * `τI::Float64`: 積分時間定数

# 例

```julia
pic = PIController(1.0, 3.0) # PIコントローラのパラメータを指定
gc = TransferFunction(pic) # これらのPIコントローラのパラメータで伝達関数を構築
```
