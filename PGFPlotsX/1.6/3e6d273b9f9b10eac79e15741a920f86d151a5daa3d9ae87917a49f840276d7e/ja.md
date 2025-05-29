```julia
Coordinates(x, y, z; meta)

```

値の行列とエッジベクトルから座標を構築します。ここで、`z[i,j]`は`x[i]`および`y[j]`に対応します。空のスキャンラインは、PGFPlotsの`mesh/ordering=x varies`オプション（デフォルト）に従って挿入されます。

```julia
x = range(0; stop = 1, length = 10)
y = range(-1; stop = 2, length = 13)
z = sin.(x) + cos.(y')
Coordinates(x, y, z)
```
