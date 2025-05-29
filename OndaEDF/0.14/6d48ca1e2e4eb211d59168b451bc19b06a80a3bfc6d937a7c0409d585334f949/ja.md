```
struct ConvertedSamples
    samples::Union{Samples,Missing}
    channel_plans::Vector{FilePlanV4}
    sensor_label::Union{String,Missing}
end
```

`EDF.Signal`のグループを表し、これらは単一の`Onda.Samples`に変換されています（例：[`edf_to_onda_samples`](@ref)によって）。`channel_plans`は変換に使用された[`FilePlanV4`s](@ref FilePlanV4)です。`sensor_label`フィールドは`channel_plans`の`sensor_label`フィールドの唯一の値です。

何らかの理由で変換が失敗した場合、`samples`は`missing`になります。変換中に発生したランタイムエラーは、`channel_plans`の`error`フィールドに格納されます。

## 変換されたサンプルを保存するための便利な関数

変換されたサンプルは*メモリ内*の`Onda.Samples`オブジェクトであり、通常は外部ストレージに永続化する必要があります。OndaEDF.jlは、`ConvertedSamples`引数を持つ[`Onda.store`](@ref)のメソッドを実装しており、ラップされた`samples`を抽出して`Onda.store`します。ラップされた`samples`が`missing`の場合、これらのメソッドは`missing`を返します。`recording`と`start`の引数を持つ`Onda.SignalV2`を返すメソッドが呼び出されると、`sensor_label`はデフォルトで伝播されます（ただし、上書きすることも可能です）。

## `EDF.File`レベルのコレクションのための便利な関数

[`edf_to_onda_samples`](@ref)を介して全体の`EDF.File`を変換すると、`Vector{ConvertedSamples}`が返されます。

[`get_plan`](@ref)関数は、`Vector{ConvertedSamples}`のプランを単一のテーブルにまとめ、`Legolas.write`に渡すのに適した形式にします。

[`get_samples`](@ref)関数は、`Vector{ConvertedSamples}`から変換されたサンプルを抽出します。デフォルトでは、この関数は`missing`のサンプルをスキップしますが、キーワード引数`skipmissing=false`を指定して呼び出すとスキップしません。
