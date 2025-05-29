```
connect_browser(
    endpoint::String = "http://localhost:9222";
    max_retries::Int = MAX_RETRIES,
    retry_delay::Real = RETRY_DELAY,
    timeout::Real = CONNECTION_TIMEOUT,
    verbose::Bool = false
)

指定されたデバッグエンドポイントでChromeブラウザに接続し、エラーハンドリングを強化します。新しいページに接続されたWSClientを返します。

# 引数

  * `endpoint::String`: ChromeデバッグエンドポイントのURL。例: `http://localhost:9222`。
  * `max_retries::Int`: Chromeを確認するための最大リトライ回数。
  * `retry_delay::Real`: リトライ間の遅延（秒単位）。
  * `timeout::Real`: 接続のタイムアウト（秒単位）。
  * `verbose::Bool`: 詳細なデバッグ情報を表示するかどうか。
```
