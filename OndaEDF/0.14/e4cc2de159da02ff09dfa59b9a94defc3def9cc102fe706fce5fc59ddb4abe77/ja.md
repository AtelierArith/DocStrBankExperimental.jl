```
edf_to_onda_samples(edf::EDF.File; kwargs...)
```

`EDF.File` から [`Vector{ConvertedSamples}`](@ref ConvertedSamples) に信号を読み込みます。これは、最初に [`plan_edf_to_onda_samples`](@ref) を介してインポートプランを策定し、その後すぐに [`edf_to_onda_samples`](@ref) を使用してこのプランを実行する便利な関数です。

!!! warning
    この関数は「迅速かつ簡易な」探索のための便利な機能として提供されています。一般的に、実行の前にプランを確認し、必要に応じて調整を行うことを強くお勧めします。


[`Vector{ConvertedSamples}`](@ref ConvertedSamples) が返されます。実行されたプランと `Onda.Samples` を抽出するには、それぞれ [`get_plan`](@ref) と [`get_samples`](@ref) を使用してください。`.samples` が `missing` である `ConvertedSamples` を調査することで、抽出されていない信号の出力を確認することを**強くお勧め**します。変換中の実行時エラーは `.channel_plans` の `:error` 列に保存され、マッチできなかった EDF 信号は `.channel_plans` の `:sensor_type`、`:channel`、または `:physical_unit` に `missing` 値を持ちます。

`EDF.Signal` のコレクションは、[`plan_edf_to_onda_samples`](@ref) を介して `Onda.Samples` にチャネルとしてマッピングされます。この関数の呼び出し元は、`labels` および `units` キーワード引数を介してプランを制御でき、これらはすべて [`plan_edf_to_onda_samples`](@ref) に転送されます。より多くの制御が必要な場合は、最初にプランを生成し、必要に応じて確認および編集し、その後 `edf_to_onda_samples` の第二引数として渡して実行します。

Onda チャネル名に変換される `EDF.Signal` ラベルは、以下の変換を受けます：

  * ラベルは空白が削除され、括弧が削除され、小文字に変換されます
  * 尾部の一般的な EDF 参照（例："ref"、"ref2" など）は削除されます
  * `+` の任意のインスタンスは `_plus_` に、`/` は `_over_` に置き換えられます
  * すべてのコンポーネント名は可能な限り「標準名」に変換されます（例：EEG にマッチしたチャネル名の "m1" は "a1" に変換されます）。

EDF フォーマットの期待に関する追加の詳細については、OndaEDF README を参照してください。

!!! warning
    返されたサンプルは整数エンコードされています。これらのサンプルがシリアライズされる場合（例：`Onda.store!` を介して）には問題ありませんが、サンプルがメモリ内で即座に分析される場合は、`Onda.decode` を呼び出してデコードし、時系列の電圧を回復してください。


```
