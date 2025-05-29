```
consensus_haplotype(
    reference::NucleotideSeq,
    variants::Union{AbstractString,AbstractPath};
    frequency::Float64=0.5,
)
```

参照から適用された `variants` からコンセンサス `Haplotype` を取得します。

# 引数

  * `reference::NucleotideSeq`: 変異が呼び出された参照ゲノムの配列
  * `variants::Union{AbstractString,AbstractPath}`: 変異が適用される変異コールファイルへのパス

# キーワード

  * `frequency::Float64=0.5`: コンセンサスの一部として含まれるために、代替位置を支持する必要がある総リードの割合。言い換えれば、これよりも高い `AF`（アレル/代替頻度）を持つVCFレコードのみがコンセンサスに寄与すると見なされます。
