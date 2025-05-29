```
select_sample(geno_selection::Geno, markers_selection:: Union{Vector{String}, InvertedIndex{Vector{String}}}) -> Geno
```

指定されたサンプル名またはそのインデックスに基づいて、`Geno`オブジェクトから遺伝的サンプルのサブセットを選択して返します。

# 引数

  * `geno_selection`: 遺伝データを含む`Geno`型または構造体。
  * `samples_selection`: サンプル名のベクターまたはサンプル名の反転インデックス

```
`geno_selection`から選択されるべきです。選択は`Geno`オブジェクト内のサンプル名に適用されます。
```

# 戻り値

  * `Geno`: 選択されたサンプルのみを含む新しい`Geno`オブジェクト、その対応する遺伝情報、

およびこれらのサンプルに関連する元の遺伝型のサブセット。 ___
