```
add_hex_anis(sim::AbstractSim; K1=0, K2=0, K3=0, name="hex")
```

シミュレーションに六角形異方性を追加します。異方性のエネルギー密度は次のように定義されます：

$$
E = K_1 \sin^2 \theta + K_2 \sin^4 \theta + K_3 \sin^6 \theta \cos 6\phi
$$

# 例

```julia
add_hex_anis(sim, K1=1e3, K2=0, K3=1e2)
```
