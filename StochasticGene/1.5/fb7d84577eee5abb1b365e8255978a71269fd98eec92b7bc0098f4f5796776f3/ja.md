```
load_data(datatype, dttype, datapath, label, gene, datacond, traceinfo, temprna, datacol=3, zeromedian=false)
```

提供された `datatype` 文字列またはシンボルに基づいて RNA またはトレースデータをロードします。

定常状態の RNA ヒストグラム、滞在時間分布、ON/OFF 状態の持続時間、蛍光トレースなど、複数のデータ形式をサポートしています。

# 引数

  * `datatype`: データタイプを説明する文字列またはシンボル（例: "rna", "tracegrid"）
  * `dttype`: 滞在時間タイプ（rnadwelltime と dwelltime のみで使用）
  * `datapath`: データファイルへのパス
  * `label`: データセットのラベル
  * `gene`: 遺伝子名
  * `datacond`: 実験条件
  * `traceinfo`: トレースメタデータのタプル
  * `temprna`: ヒストグラム正規化のための整数除数
  * `datacol`: 抽出するトレースデータの列（デフォルト = 3）
  * `zeromedian`: true の場合、フィッティング前に各トレースをゼロ中心にする（デフォルト = false）

# 戻り値

  * 具体的なデータ構造のサブタイプ（例: `RNAData`, `TraceRNAData`, `DwellTimeData`）

# 例外

  * `ArgumentError` は `datatype` がサポートされていない場合にスローされます
