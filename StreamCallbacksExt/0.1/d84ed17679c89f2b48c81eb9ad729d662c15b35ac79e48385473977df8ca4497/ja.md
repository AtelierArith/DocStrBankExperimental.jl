```
extract_tokens(::StreamCallbacks.AnthropicStream, chunk::StreamCallbacks.AbstractStreamChunk)
```

Anthropicストリームチャンクからトークン数を抽出します。使用情報を伴うmessage_startイベントと出力トークンを伴うcompletionイベントの両方を処理します。
