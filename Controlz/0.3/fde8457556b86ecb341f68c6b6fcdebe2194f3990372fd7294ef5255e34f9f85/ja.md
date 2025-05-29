```
pc = PController(Kc)
```

比例（P）コントローラを構築するには、以下の伝達関数表現で定義されたコントローラゲインを指定します：

$$
g_c(s)=K_c
$$

# 引数

  * `Kc::Float64`: コントローラゲイン

# 例

```julia
pc = PController(1.0) # Pコントローラゲインを指定
gc = TransferFunction(pc) # このPコントローラゲインで伝達関数を構築
```
