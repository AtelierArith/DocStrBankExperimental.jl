EEGデータ型のための構造体。EEGは単にラベル付きの時系列のコレクションとして考えられます。

# フィールド

  * `signals::Dict{String, TimeSeries}`: 信号ラベル（文字列）を浮動小数点値の配列にマッピングする辞書。

# コンストラクタ

`EEG(file::String; id::String="")`: EDFファイル（`file`）から`EEG`をインスタンス化します。

# 例

```julia
eeg_data = EEG("path/to/edf_data/data.edf")
```
