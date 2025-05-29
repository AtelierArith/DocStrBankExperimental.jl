```
INFEASIBLE_OR_UNBOUNDED::TerminationStatusCode
```

[`TerminationStatusCode`](@ref) 列挙型のインスタンスです。

## 概要

アルゴリズムは、問題が非実現可能または無限大であることを証明したため停止しましたが、2つのケースを区別していません。

2つのケースを区別するには、目的の感覚を [`FEASIBILITY_SENSE`](@ref) に設定し、問題を再解決します。プライマル実現可能点が存在する場合、元の問題は無限大です。プライマル実現可能点が存在しない場合、元の問題は非実現可能です。
