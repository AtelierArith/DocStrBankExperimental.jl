```
compose(t, trans1::KinematicTransformation, trans2::KinematicTransformation)
```

時間 `t` において `trans2` を適用し、その後に `trans1` を適用することによって得られる変換を返します。

これはおそらく `ConstantAffineMap` を返しますが、より特定の変換を返す場合もあります。例えば、2つの `ConstantLinearMap` を組み合わせると、新しい `ConstantLinearMap` が得られます。
