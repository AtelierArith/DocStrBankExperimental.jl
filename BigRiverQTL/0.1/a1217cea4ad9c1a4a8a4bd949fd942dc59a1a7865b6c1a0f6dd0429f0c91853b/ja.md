```
select_marker(geno_selection::Geno, markers_selection:: Union{Vector{String}, InvertedIndex{Vector{String}}}) -> Geno
```

指定されたマーカー名またはそのインデックスに基づいて、`Geno`オブジェクトから遺伝子マーカーのサブセットを選択して返します。

# 引数

  * `geno_selection`: 遺伝子データを含む`Geno`型または構造体。
  * `markers_selection`: マーカー名のベクターまたはマーカー名の反転インデックス

```
`geno_selection`から選択されるべきです。選択は`Geno`オブジェクト内のマーカー名に適用されます。
```

# 戻り値

  * `Geno`: 選択されたマーカーのみを含む新しい`Geno`オブジェクト、その対応する遺伝情報、

およびこれらのマーカーに関連する元の遺伝型のサブセット。
