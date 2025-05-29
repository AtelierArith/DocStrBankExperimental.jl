```
extract_stop_sequence(::StreamCallbacks.OpenAIStream, chunk::StreamCallbacks.AbstractStreamChunk)
```

OpenAIストリームチャンクから停止シーケンスを抽出します。delta.stop*sequenceとfinish*reason="stop"の両方を処理します。
