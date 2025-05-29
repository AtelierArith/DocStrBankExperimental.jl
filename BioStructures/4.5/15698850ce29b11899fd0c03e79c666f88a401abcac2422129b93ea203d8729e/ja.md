```
psiangle(res, res_next)
psiangle(chain, res_id)
```

`AbstractResidue`のpsi角をラジアンで計算します。

引数は、残基と次の残基、またはチェーンと残基IDとしての位置のいずれかです。最初の残基（または指定されたインデックスの残基）には、原子"N"、"CA"、および"C"が必要で、次の残基には原子"N"が必要です。角度は-πからπの範囲です。
