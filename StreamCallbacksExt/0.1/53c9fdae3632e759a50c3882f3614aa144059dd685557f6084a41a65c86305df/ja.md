```
extract_tokens(::StreamCallbacks.OpenAIStream, chunk::StreamCallbacks.AbstractStreamChunk)
```

OpenAIストリームチャンクからトークン数を抽出します。以下を処理します：

  * プロンプト*tokensおよびcompletion*tokensを含むレガシーフォーマット
  * キャッシュヒット/ミス統計
  * 詳細なトークン内訳（cached*tokens、audio*tokens）
  * ストリームの終わりにおける統合使用統計
