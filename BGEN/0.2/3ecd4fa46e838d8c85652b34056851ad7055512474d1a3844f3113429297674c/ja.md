```
minor_allele_dosage!(b::Bgen, v::BgenVariant; T=Float32,
mean_impute=false, clear_decompressed=false)
```

`Bgen` 構造体と `BgenVariant` を与えられたとき、マイナーアレルの用量を計算します。結果は `v.genotypes.dose` に格納され、`clear!(v)` を使用してクリアできます。

  * `T`: 結果の型
  * `mean_impute`: 欠損値を非欠損値の平均で補完する
  * `clear_decompressed`: 実行後に `true` に設定されている場合、解凍されたバイト文字列をクリアします
