```
BlockDiagonalOperator(M1, M2, ..., Mn; S = promote_type(storage_type.(M1, M2, ..., Mn)))
```

Creates a block-diagonal linear operator:

```
[ M1           ]
[    M2        ]
[       ...    ]
[           Mn ]
```

Change `S` to use LinearOperators on GPU.
