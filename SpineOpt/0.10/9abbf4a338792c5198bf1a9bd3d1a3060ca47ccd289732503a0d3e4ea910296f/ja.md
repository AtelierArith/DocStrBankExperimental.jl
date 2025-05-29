```
roll_temporal_structure!(m[, window_number=1]; rev=false)
```

与えられたSpineOptモデルの時間構造を、`roll_forward`パラメータの値と等しい期間だけ前方にロールします。`roll_forward`が配列の場合、`window_number`はその配列内の位置または連続する位置を示す`Integer`または`UnitRange`として指定できます。

`rev`が`true`の場合、構造は前方ではなく後方にロールされます。
