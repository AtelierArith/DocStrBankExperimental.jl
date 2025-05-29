```
PopData
    metadata::PopDataInfo
    genodata::DataFrame
```

PopGen人口遺伝学エコシステムで使用されるデータ構造です。PopDataに渡すために手動でテーブルを作成することは**強く**推奨されていません。代わりに、提供されたファイルインポータやユーティリティを使用してください。

```
- `metadata` データ情報のPopDataInfo
    - `samples` - データ内のサンプル数
    - `sampleinfo` - サンプル名、集団、倍数性などのDataFrame
    - `loci` - データ内のロキ数
    - `locusinfo` - ロキ名、染色体、物理的位置などのDataFrame
    - `populations` - データ内の集団数
    - `ploidy` - データ内に存在する倍数性
    - `biallelic` - すべてのマーカーが二倍体であるかどうか
- `genodata` サンプル遺伝子型レコードのDataFrame
    - `name` - 個体/サンプル名 [`PooledArray`]
    - `population` - 集団名 [`PooledArray`]
    - `locus` - ロキ名 [`PooledArray`]
    - `genotype` - 遺伝子型の値 [`NTuple{N,Signed}`]
```
