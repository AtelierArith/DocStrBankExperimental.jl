```
tokenizer(sp::SentencePieceModel,text::AbstractString)
```

すべての前処理ステップを実行し、`decode_forward` と `decode_backward` を実行して、トークンを Array{String,1} として出力します。
