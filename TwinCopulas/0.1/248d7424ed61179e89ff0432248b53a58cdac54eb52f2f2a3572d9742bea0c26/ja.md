```
CuadrasAugeCopula{P}
```

フィールド:

```
- α::Real - パラメータ
```

コンストラクタ

```
CuadrasAugeCopula(α)
```

二変量Cuadras Augeコピュラは、$\alpha \in [0,1]$でパラメータ化されています。これは、ピカンズ依存関数を持つ極値コピュラです:

$$
A(t) = \max\{t, 1-t \} + (1-\theta)\max\{t, 1-t\}
$$

参考文献:

  * [Mai2017](@cite) コピュラのシミュレーション: 確率モデル、サンプリングアルゴリズム、および応用。2017年。
