```
KrylovKitExp([ham; kw...])
```

`EvolutionSolver`は、KrylovKit.jlの`exponentiate`関数を使用して波動関数ベクトルを進化させます。このソルバーは、大規模で疎な時間依存ハミルトニアンに対して便利です。

## 引数

  * `ham`: システムのハミルトニアン。`Operator`またはその行列であることができます。
  * `kw...`: `exponentiate`に渡されるキーワード引数。
