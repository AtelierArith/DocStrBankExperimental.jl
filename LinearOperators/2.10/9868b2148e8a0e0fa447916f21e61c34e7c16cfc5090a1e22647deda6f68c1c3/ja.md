```
BlockDiagonalOperator(M1, M2, ..., Mn; S = promote_type(storage_type.(M1, M2, ..., Mn)))
```

ブロック対角線形演算子を作成します：

```
[ M1           ]
[    M2        ]
[       ...    ]
[           Mn ]
```

`S`を使用してGPU上のLinearOperatorsに変更します。
