```
pcalg(t, p::Float64, test::typeof(gausscitest); kwargs...)
```

テーブル形式の入力データ t に対して PC アルゴリズムを実行し、Fisher の z 変換を使用して条件付き独立性をテストするために p 値 p を使用します。
