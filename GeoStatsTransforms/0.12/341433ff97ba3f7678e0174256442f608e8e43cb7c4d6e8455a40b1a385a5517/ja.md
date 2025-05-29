```
Transfer(domain)
Transfer([g₁, g₂, ..., gₙ])
```

ソースドメインからターゲット`domain`に変数`var₁`、`var₂`、..., `varₙ`を転送します。あるいは、変数を幾何学的形状`g₁`、`g₂`、..., `gₙ`に転送します。

# 例

```julia
Transfer(CartesianGrid(10, 10))
Transfer(rand(Point, 100))
```
