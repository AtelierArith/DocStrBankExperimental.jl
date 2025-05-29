```
genotypes(data::PopData, samplelocus::Pair{String, String}) ::DataFrame
genotypes(data::PopData, samplelocus::Pair{Vector{String}, String}) ::DataFrame
genotypes(data::PopData, samplelocus::Pair{String, Vector{String}}) ::DataFrame
```

`PopData`オブジェクト内の1つまたは複数のサンプル/ロキの遺伝子型または遺伝子型のデータフレームを返します。`samples => loci`の`Pair`表記を使用します。

### 例

```
cats = @nancycats;
genotypes(cats, "N115" => "fca8")
genotypes(cats, ["N115", "N7"] => "fca8")
genotypes(cats, "N115" => ["fca8", "fca37"])
genotypes(cats, ["N1", "N2"] => ["fca8", "fca37"])
```
