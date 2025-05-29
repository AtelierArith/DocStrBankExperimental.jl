```
variable_flow(
    wm::AbstractNCModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

すべてのノード接続コンポーネント（例：パイプ、ポンプ）に対して、サブネットワーク（または時間）インデックス `nw` で制約付き（デフォルト）または制約なしのフロー変数を作成します。例えば、`q_pipe[a]` は `a` が `pipe` の場合、`q_pump[a]` は `a` が `pump` の場合です。これは、フローディレクションベースのネットワークモデルの定式化には使用されません。
