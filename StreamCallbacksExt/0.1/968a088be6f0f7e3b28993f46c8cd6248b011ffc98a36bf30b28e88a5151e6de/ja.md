```
StreamCallbackWithTokencounts(; 
    out=stdout, 
    flavor=nothing, 
    chunks=StreamChunk[], 
    verbose=false,
    throw_on_error=false,
    kwargs=NamedTuple(),
    total_tokens=TokenCounts(),
    model=nothing,
    token_formatter=default_token_formatter,
    content_formatter=default_content_formatter,
    timing=RunInfo()
)
```

トークンの使用状況、コスト、およびタイミング情報を追跡するストリームコールバック。

# 引数

  * `out`: 出力IOストリーム（デフォルト: stdout）
  * `flavor`: ストリームフォーマットハンドラー（OpenAI/Anthropic）
  * `chunks`: ストリームチャンクを格納するベクター
  * `verbose`: 詳細ログを有効にする
  * `throw_on_error`: エラーをスローするかどうか
  * `kwargs`: 追加のキーワード引数
  * `total_tokens`: 累積トークン数
  * `model`: モデル識別子
  * `token_formatter`: トークン統計をフォーマットする関数
  * `content_formatter`: ストリーミングされたコンテンツをフォーマットする関数
  * `timing`: タイミング情報

# 例

cb = StreamCallbackWithTokencounts(     out = stdout,     flavor = StreamCallbacks.OpenAIStream() )
