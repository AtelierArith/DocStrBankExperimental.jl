```
extract_model(::StreamCallbacks.AnthropicStream, chunk::StreamCallbacks.AbstractStreamChunk)
```

Anthropicストリームチャンクからモデル識別子を抽出します。特にmessage_startイベントから。
