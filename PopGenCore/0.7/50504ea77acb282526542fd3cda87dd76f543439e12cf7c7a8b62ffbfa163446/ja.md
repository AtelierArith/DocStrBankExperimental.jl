```
genotypes(data::PopData, samplelocus::String)
```

`PopData`オブジェクト内のサンプル（またはローカス）のすべての遺伝子型のベクトルを返します。

```
cats = @nancycats
genotypes(cats, "N115")
genotypes(cats, "fca8")

```
