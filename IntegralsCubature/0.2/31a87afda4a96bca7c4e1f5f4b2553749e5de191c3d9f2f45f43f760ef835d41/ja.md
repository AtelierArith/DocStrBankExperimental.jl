```
CubatureJLp()
```

Cubature.jlによる多次元p適応積分。この方法は、収束が達成されるまで、キュバチュアルールの次数を繰り返し倍増させることに基づいています。使用されるキュバチュアルールは、クレンズホー・カーティスの数値積分ルールのテンソル積です。`error_norm`は、ベクトル値の被積分関数に対する収束基準を指定します。デフォルトは`Cubature.INDIVIDUAL`で、他のオプションは`Cubature.PAIRED`、`Cubature.L1`、`Cubature.L2`、または`Cubature.LINF`です。
