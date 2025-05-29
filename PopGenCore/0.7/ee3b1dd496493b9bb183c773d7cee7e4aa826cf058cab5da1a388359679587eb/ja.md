```
plink(data::PopData; filename::String)
```

バイアレリック `PopData` オブジェクトを PLINK `.ped` 形式で書き出し、対応する `.fam` ファイルを作成します。遺伝子型は PLINK 標準でコーディングされています：

  * 整数はアレルを表します
  * `0` は欠損を表します
  * 6 列目以降は、2 つの数字が一対の二倍体遺伝子型を示します。

## 例

```julia
sharks = dropmultiallelic(@gulfsharks) ;
plink(sharks, filename = "biallelic_sharks.ped")
```
