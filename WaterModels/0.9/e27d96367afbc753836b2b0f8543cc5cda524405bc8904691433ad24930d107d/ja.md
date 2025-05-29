```
variable_reservoir_flow(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

ネットワーク内のサブネットワーク（または時間）インデックス `nw` に対して、貯水池のための制約付き（デフォルト）または制約なしの流出体積流量変数を作成します。つまり、`q_reservoir[i]` は `reservoir` の `i` に対してです。これらの変数は常に非負であることに注意してください。なぜなら、各貯水池に対して、流入流量は決して存在しないからです。
