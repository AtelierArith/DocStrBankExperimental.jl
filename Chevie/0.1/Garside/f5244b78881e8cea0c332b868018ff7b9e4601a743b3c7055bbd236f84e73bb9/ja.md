`GarsideMonoid{T}` は Garside モノイドの抽象型であり、`T` は単純な型です。このようなモノイド `M` は、`LocallyGarsideMonoid` と同じメソッドを実装する必要がありますが、`isrightascent(M,a)` は自動的に `isleftdescent(M,\(M,a,M.δ),i)` として定義されます。

実装にはフィールド `M.δ`、`M.stringδ` が必要です。

区間モノイドにはフィールド `M.orderδ` が必要です。
