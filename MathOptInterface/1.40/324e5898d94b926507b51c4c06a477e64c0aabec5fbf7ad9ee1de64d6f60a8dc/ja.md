```
LOCALLY_INFEASIBLE::TerminationStatusCode
```

[`TerminationStatusCode`](@ref) 列挙型のインスタンスです。

## 概要

アルゴリズムは非実行可能な点に収束したか、実行可能な解を見つけることなく探索を完了しましたが、実行可能な解が存在しないという保証はありません。

実行可能なプライマル解が存在することがわかっている場合は、[`VariablePrimalStart`](@ref) を使用してソルバーに実行可能な開始点を提供してください。
