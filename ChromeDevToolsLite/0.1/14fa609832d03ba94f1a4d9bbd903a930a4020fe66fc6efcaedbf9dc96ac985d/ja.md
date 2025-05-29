```
ensure_browser_available(
    endpoint::String;
    max_retries::Int = MAX_RETRIES,
    retry_delay::Real = RETRY_DELAY,
    verbose::Bool = false
)

指定されたエンドポイントでChromeがデバッグモードで実行されているかどうかを確認します。指定された`retry_delay`で`max_retries`回まで再試行します。Chromeがデバッグポートで応答している場合は`true`を返します。

# 引数

  * `endpoint::String`: ChromeデバッグエンドポイントのURL。例: `http://localhost:9222`。
  * `max_retries::Int`: Chromeを確認するための最大再試行回数。
  * `retry_delay::Real`: 再試行間の遅延（秒単位）。
  * `verbose::Bool`: 詳細なデバッグ情報を印刷するかどうか。
```
