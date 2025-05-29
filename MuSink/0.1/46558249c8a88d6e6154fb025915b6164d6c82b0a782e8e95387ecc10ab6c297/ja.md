```
Problem(targets [; cost, penalty, references, reference_mass])
```

MuSink問題のデフォルトコンストラクタです。

引数`targets`と`references`は、タイプ`Dict{Node, Array{Float64, 3}}`であることが期待されており、ツリーの各ノードにターゲットおよびリファレンスの測定値を割り当てます。`reference_mass`が指定されている場合、リファレンスはその積測定値が`reference_mass`になるようにスケーリングされます。
