```
mul!(result, Ct::Transpose{Int, CopyMatrix}, A)
```

行列 `A` に対してコピー行列の転置を左から掛けることは、下三角インデックスに対応する `A` の行を保持することと同等です。
