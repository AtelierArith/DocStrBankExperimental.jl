```
LotkaVolterra(;kwargs)
```

ロトカ・ヴォルテラ捕食者-被食者モデルをプロセスモデルとして使用してサンプルデータセットを作成します：

````
```math
\frac{dN}{dt} = rN - \alpha NP \
\frac{dP}{dt} = \theta\alpha NP - mP
```
````

および平均0、標準偏差σの正規分布に従う観測誤差。

```
# kwargs
- `plot`: 関数はプロットを返しますか？ デフォルトは `true` です。
- `seed`: 再現可能な例を作成するための観測誤差のシード。 デフォルトは `123` です。
- `datasize`: 生成される時間ステップの数。 デフォルトは `60` です。
- `T`: 最大時間範囲。 デフォルトは `3.0` です。
- `sigma`: 観測誤差の標準偏差。 デフォルトは `0.075` です。
```
