```
omegaangle(res, res_previous)
omegaangle(chain, res_id)
```

`AbstractResidue`のオメガ角をラジアンで計算します。

引数は、残基と前の残基、またはチェーンと残基IDとしての位置のいずれかである必要があります。最初の残基（または指定されたインデックスの残基）は、原子"N"と"CA"を必要とし、前の残基は原子"CA"と"C"を必要とします。角度は-πからπの範囲です。
