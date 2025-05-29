```
consensus_record(
    reference::Union{AbstractString,AbstractPath},
    variants::Union{AbstractString,AbstractPath};
    frequency::Float64=0.5,
    prefix::Union{AbstractString,Nothing}=nothing,
)
```

最初の配列に適用された `variants` からのコンセンサス `FASTA.Record` を取得します。

# 引数

  * `reference::Union{AbstractString,AbstractPath}`: 変異が呼び出された参照ゲノムへのパス。最初の配列のみが使用されます。
  * `variants::Union{AbstractString,AbstractPath}`: 変異が適用される変異コールファイルへのパス

# キーワード

  * `frequency::Float64=0.5`: コンセンサスの一部として含まれるために、代替位置を支持する必要がある総リードの割合。言い換えれば、`AF`（アレル/代替頻度）がこれより高い VCF レコードのみがコンセンサスに寄与すると見なされます。
  * `prefix::Union{AbstractString,Nothing}=nothing`: 出力レコードに付ける名前。デフォルトでは、出力レコードの名前は入力レコードの名前に `_CONSENSUS` が追加されたものになります。`prefix` が指定されている場合、出力レコードの名前は `$(prefix)_CONSENSUS` になります。
