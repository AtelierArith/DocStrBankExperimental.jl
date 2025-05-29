```
streamed_request!(cb::AbstractStreamCallback, url, headers, input; kwargs...)
```

POSTストリーミングリクエストのエンドツーエンドラッパー。リクエストの結果でコールバックオブジェクト（`cb.chunks`）をインプレースで修正します。最終的にレスポンスオブジェクトの`body`を構築し、それを`resp.body`に書き込みます。

レスポンスオブジェクトを返します。

# 引数

  * `cb`: コールバックオブジェクト。
  * `url`: リクエストを送信するURL。
  * `headers`: リクエストと共に送信するヘッダー。
  * `input`: リクエストボディを含むバッファ。
  * `kwargs`: 追加のキーワード引数。
