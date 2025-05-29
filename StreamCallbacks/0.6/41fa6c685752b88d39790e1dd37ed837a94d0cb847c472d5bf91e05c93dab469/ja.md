```
StreamCallback
```

ストリーミングメッセージの最も簡単なコールバックで、`out`で定義された出力ストリームにコンテンツを印刷するだけです。ストリーミングが終了すると、チャンクからレスポンスボディを構築し、APIからの通常のレスポンスのように返します。

より複雑なユースケースの場合は、自分自身の`callback`を定義できます。詳細については、以下のインターフェースの説明を参照してください。

# フィールド

  * `out`: 出力ストリーム、例えば`stdout`やパイプ。
  * `flavor`: プロバイダーによって異なる可能性のあるストリームフレーバー、例えば`OpenAIStream`や`AnthropicStream`。
  * `chunks`: 受信した`StreamChunk`チャンクのリスト。
  * `verbose`: 詳細情報を印刷するかどうか。DEBUGロギングを有効にすると、チャンクが到着するたびに表示されます。
  * `throw_on_error`: ストリーミングレスポンスにエラーメッセージが検出された場合にエラーをスローするかどうか。
  * `kwargs`: ユースケースに必要なカスタムキーワード引数。

# インターフェース

  * `StreamCallback(; kwargs...)`: `StreamCallback`オブジェクトのコンストラクタ。
  * `streamed_request!(cb, url, headers, input)`: POSTストリーミングリクエストのエンドツーエンドラッパー。

`streamed_request!`は以下で構成されています：

  * `extract_chunks(flavor, blob)`: 受信したSSEブロブからチャンクを抽出します。`StreamChunk`のリストと次のスピルオーバー（メッセージが不完全な場合）を返します。
  * `callback(cb, chunk)`: 印刷されるチャンクを処理します。

      * `extract_content(flavor, chunk)`: チャンクからコンテンツを抽出します。
      * `print_content(out, text)`: コンテンツを出力ストリームに印刷します。
  * `is_done(flavor, chunk)`: ストリームが完了しているかどうかを確認します。
  * `build_response_body(flavor, cb)`: チャンクからレスポンスボディを構築し、APIからの標準レスポンスを受信するかのように模倣します。

独自のコールバックを実装したい場合は、インターフェース関数のための独自のメソッドを作成できます。例えば、ストリーミングされたチャンクを特定のシンクやチャネルに印刷したい場合は、`print_content`のためだけのシンプルなメソッドを定義できます。

# 例

```julia
using PromptingTools
const PT = PromptingTools

# 最も簡単な使用法、テキストをストリーミングする場所を提供するだけです（コールバックを自動的に構築します）
msg = aigenerate("1から100まで数えます。"; streamcallback = stdout)

streamcallback = PT.StreamCallback() # すべてのチャンクを記録
msg = aigenerate("1から100まで数えます。"; streamcallback)
# これにより、`streamcallback.chunks`で各チャンクを検査できます

# デバッグ用に各チャンクの詳細を含む詳細な出力を取得
streamcallback = PT.StreamCallback(; verbose=true, throw_on_error=true)
msg = aigenerate("1から10まで数えます。"; streamcallback)
```

注意: `StreamCallback`オブジェクトを`aigenerate`に提供すると、`flavor`フィールドを指定しない限り、`configure_callback!`を介してそれを構成し、必要な`api_kwargs`を設定します。特定の`flavor`を持つ`StreamCallback`を提供した場合、すべての構成はユーザーに任せます（例えば、正しい`api_kwargs`を提供する必要があります）。
