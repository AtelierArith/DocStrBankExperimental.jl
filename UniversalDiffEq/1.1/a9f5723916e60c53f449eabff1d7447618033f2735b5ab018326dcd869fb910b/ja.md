```
LorenzLotkaVolterra(;kwargs)
```

ロレンツ・ロトカ-ヴォルテラモデルをプロセスモデルとして使用してサンプルデータセットを作成します：

````
```math
rac{dx}{dt} = rx(1-rac{x}{K}) - lpha xy + gz\
rac{dy}{dt} = 	hetalpha xy - my\
rac{dz}{dt} = l(w-z)\
rac{dw}{dt} = z(ho-s) 0 w\
rac{ds}{dt} = zw-eta s
```
````

および観測誤差は平均0、標準偏差σ_{obs}に従う正規分布に従います。

```
# kwargs
- `plot`: 関数はプロットを返しますか？ デフォルトは`true`です。
- `seed`: 再現可能な例を作成するための観測誤差のシード。デフォルトは`123`です。
- `datasize`: 生成される時間ステップの数。デフォルトは`60`です。
- `T`: 最大時間範囲。デフォルトは`3.0`です。
- `sigma`: 観測誤差の標準偏差。デフォルトは`0.075`です。
```
