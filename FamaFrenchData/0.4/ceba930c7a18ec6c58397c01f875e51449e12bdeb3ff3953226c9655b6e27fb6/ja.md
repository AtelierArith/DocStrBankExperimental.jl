```
readFamaFrench(ffn;kwargs...)
```

`ffn` はテーブル名（この場合、ウェブから取得されます）またはローカルファイルへのパスです。`kwargs` は `CSV.File` に渡されます。欠損値（`-99.99` または `-999`）は `missing` に置き換えられます。

返されるのは3つの部分です：

```
- `tables::Vector{DataFrame}` - 抽出されたテーブル

- `tablenotes::Vector{String}` - テーブルに関するメモ

- `filenotes::String` - ファイルの先頭にあるメモ
```

使用例：

```julia
using DataFrames, FamaFrenchData

# Fama-French 3因子を読み込む（毎月および年次）
tables, tablenotes, filenotes = readFamaFrench("F-F_Research_Data_Factors")

# Fama-French 3因子を読み込む（毎日）
tablesd, tablenotesd, filenotesd = readFamaFrench("F-F_Research_Data_Factors_Daily")

# 25のサイズ-B/Mポートフォリオを読み込む（毎月および年次）
tables25, tablenotes25, filenotes25 = readFamaFrench("25_Portfolios_5x5")
```
