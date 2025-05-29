```
with_retry(f::Function; max_retries::Int = MAX_RETRIES, retry_delay::Real = RETRY_DELAY, verbose::Bool = false)
```

関数 `f` をリトライロジックで実行します。`max_retries` 回まで `f` を実行しようとし、試行の間に `retry_delay` 秒待ちます。

# 引数

  * `f::Function`: リトライで実行する関数。
  * `max_retries::Int`: 最大リトライ回数。
  * `retry_delay::Real`: リトライ間の遅延（秒）。
  * `verbose::Bool`: 詳細なデバッグ情報を表示するかどうか。

# 戻り値

  * 成功した場合の `f` の実行結果。

# 例外

  * すべてのリトライが失敗した場合に遭遇した最後の例外。
