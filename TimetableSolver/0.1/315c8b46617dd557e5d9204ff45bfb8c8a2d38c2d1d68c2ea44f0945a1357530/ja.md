```
get_solution(m::Model, modelvars::OrderedDict, vardata::VariableData)::Tuple{OrderedDict{Int,Int},MOI.TerminationStatusCode}
```

与えられたモデル `m` を解決し、モデル変数 `modelvars` と変数データ `vardata` を使用して解の値にアクセスした後、解とステータスコードを返します。

# 注意事項

  * モデルは、ステータスコードが [`MOI.OPTIMAL`](https://jump.dev/JuMP.jl/stable/moi/reference/models/#MathOptInterface.TerminationStatusCode) の場合にのみ最適に解決されます。
  * 解は、変数からその値へのマッピングです（両方とも整数として）。
