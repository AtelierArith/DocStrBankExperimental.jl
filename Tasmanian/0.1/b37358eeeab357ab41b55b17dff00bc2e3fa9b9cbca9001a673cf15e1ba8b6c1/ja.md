```
evaluateHierarchicalFunctions(tsg::TasmanianSG, x)
```

は、ドメイン内の一連の点で階層関数を評価し、結果を持つ行列を返します。

x: tsg.dimensions 行 x getNumPoints(tsg) 列の行列     列は重みを評価するための点を示します。

output: 次の次元の行列を返します          shape == [x.shape[0], getNumPoints()]         点での基底関数の値。
