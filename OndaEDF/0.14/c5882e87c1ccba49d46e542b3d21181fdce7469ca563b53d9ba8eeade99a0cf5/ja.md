```
plan_edf_to_onda_samples(header, seconds_per_record; labels=STANDARD_LABELS,
                         units=STANDARD_UNITS)
plan_edf_to_onda_samples(signal::EDF.Signal, args...; kwargs...)
```

EDF信号をOnda形式に変換する計画を策定します。これは、信号ヘッダーのすべての列に加えて、この信号の`Onda.SamplesInfo`の追加列と、ここで渡される`seconds_per_record`を持つTables.jlの行を返します。

ラベルが一致しない場合、`channel`および`sensor_type`列は`missing`になります。他の`SamplesInfo`列の動作は未定義であり、現在はmissingに設定されていますが、将来のバージョンで変更される可能性があります。

プロセスで発生するエラーはすべて`SampleInfoError`としてラップされ、`error`列に文字列としてバックトレースと共に印刷されます。

## EDFラベルとOndaラベルの一致

`labels`キーワード引数は、Ondaの`channel`および信号`sensor_type`がEDFラベルからどのように抽出されるかを決定します。

ラベルは、`signal_names => channel_names`ペアの反復可能なものとして指定されます。`signal_names`は信号名の反復可能なものであり、その最初のものがOndaの`sensor_type`として使用される標準名です。`channel_names`の各要素は、1つのチャネルの仕様を提供し、文字列または`canonical_name => alternates`ペアのいずれかであることができます。`alternates`の出現は、生成されたチャネルラベル内で`canonical_name`に置き換えられます。

一致は*完全に*チャネル名によって決定されます。一致する際、信号名はチャネル名と一致する前にプレフィックスとして出現する信号名を削除するためにのみ使用されます（例: "[ECG] AVL"）。詳細については[`match_edf_label`](@ref)を参照し、デフォルトラベルについては`OndaEDF.STANDARD_LABELS`を参照してください。

例として、ECG信号のデフォルトラベルの（サブセット）を以下に示します：

```julia
["ecg", "ekg"] => ["i" => ["1"], "ii" => ["2"], "iii" => ["3"],
                   "avl"=> ["ecgl", "ekgl", "ecg", "ekg", "l"],
                   "avr"=> ["ekgr", "ecgr", "r"], ...]
```

一致は`labels`がペアを反復する順序で行われ、最初の一致で停止します。信号があいまいな場合に警告はありません（ただし、これは将来のバージョンで変更される可能性があります）。
