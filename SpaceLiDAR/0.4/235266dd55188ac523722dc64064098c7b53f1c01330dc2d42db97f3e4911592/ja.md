```
to_egm2008!(table)
```

EGM2008ジオイドモデルを使用して楕円体高をジオイド高に変換します。`:latitude`、`:longitude`、および`:height`の列を持つ[`points`](@ref)から生成されたテーブルを前提としています。`:height`列はジオイド高で上書きされます。
