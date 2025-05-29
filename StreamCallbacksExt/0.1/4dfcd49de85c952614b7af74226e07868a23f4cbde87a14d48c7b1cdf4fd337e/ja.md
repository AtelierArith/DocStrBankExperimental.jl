```
StreamCallbackWithHooks(; kwargs...)
```

トークンカウントとさまざまなイベントのカスタマイズ可能なフックを組み合わせたストリームコールバックです。

# フィールド

  * `out`: 出力IOストリーム（デフォルト: stdout）
  * `flavor`: ストリームフォーマットハンドラ（OpenAI/Anthropic）
  * `chunks`: ストリームチャンクを格納するベクター
  * `verbose`: 詳細ログを有効にする
  * `throw_on_error`: エラーをスローするかどうか
  * `kwargs`: 追加のキーワード引数
  * `total_tokens`: 累積トークンカウント
  * `model`: モデル識別子
  * `token_formatter`: トークン統計をフォーマットする関数
  * `timing`: タイミング情報

# フック

  * `content_formatter`: コンテンツテキストを処理してフォーマットする関数
  * `on_meta_usr`: ユーザートークンカウント/メタデータのハンドラ
  * `on_meta_ai`: AIトークンカウント/メタデータのハンドラ
  * `on_error`: エラーハンドラ
  * `on_done`: 完了ハンドラ
  * `on_start`: スタートハンドラ

# 例

```julia
cb = StreamCallbackWithHooks(
    on_meta_ai = (tokens, cost, elapsed) -> println("AI: $(tokens.output) tokens")
)
```
