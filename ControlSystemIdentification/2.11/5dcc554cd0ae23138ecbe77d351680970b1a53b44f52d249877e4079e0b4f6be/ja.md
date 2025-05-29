```
noise_model(sys::AbstractPredictionStateSpace)
```

システムを駆動するノイズのモデル `v` を返します。

$$
x' = Ax + Bu + Kv\\
y = Cx + Du + v
$$

このモデルは `u` を無視し、次のように与えられます。

$$
x' = Ax + Kv\\
y = Cx + v
$$

「イノベーション形式」とも呼ばれます。この関数は `ControlSystemsBase.innovation_form` を呼び出します。
