```julia
launch(link)

```

`taker` タスクを構築し、それを `link` にバインドします。`taker` タスクはデータを読み取り、`link` から `missing` が読み取られるまで情報メッセージを印刷します。
