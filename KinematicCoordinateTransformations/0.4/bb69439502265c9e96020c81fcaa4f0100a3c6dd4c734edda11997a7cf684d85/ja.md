```
ConstantAffineMap
```

`x_target = A*x_source + b` の形の変換を記述する `struct` であり、`x_source` の時間微分も含まれます。ここで、`A` と `b` は時間に対して定数です。

`ConstantAffineMap` は通常、他の `KinematicTransformation` から内部的に構築されます。
