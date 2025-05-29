```
MOCopula{P}
```

フィールド:

```
- λ1::Real - パラメータ
- λ2::Real - パラメータ
- λ12::Real - パラメータ
```

コンストラクタ

```
MOCopula(θ)
```

二変量マーシャル-オルキンコピュラは、$\lambda_i \in [0,\infty), i = 1, 2, \{1,2\}$ によってパラメータ化されます。これは、ピカンズ依存関数を持つ極値コピュラです:

$$
A(t) = \frac{\lambda_1 (1-t)}{\lambda_1 + \lambda_{1,2}} + \frac{\lambda_2 t}{\lambda_2 + \lambda_{1,2}} + \lambda_{1,2}\max\left \{\frac{1-t}{\lambda_1 + \lambda_{1,2}}, \frac{t}{\lambda_2 + \lambda_{1,2}}  \right \} 
$$

参考文献:

  * [Mai2017](@cite) コピュラのシミュレーション: 確率モデル、サンプリングアルゴリズム、および応用。2017年。
