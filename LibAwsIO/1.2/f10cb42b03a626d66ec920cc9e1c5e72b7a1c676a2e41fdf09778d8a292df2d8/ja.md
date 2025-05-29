```
aws_retry_strategy_schedule_retry(token, error_type, retry_ready, user_data)
```

バックオフおよびトークンベースの戦略に基づいてリトライをスケジュールします。retry_readyは、リトライが実行の準備ができたとき、またはアプリケーションのシャットダウンによりキャンセルされたときに呼び出されます。

この関数は、例えばサーキットブレーカーが開いている場合など、リトライ試行を拒否するためにエラーを返すことがあります。この場合、ユーザーは呼び出し元への呼び出しを失敗させるべきです。

error*typeは帳簿管理に使用されます。 [`aws*retry*error*type`](@ref)の上のコメントを参照してください。

### プロトタイプ

```c
int aws_retry_strategy_schedule_retry( struct aws_retry_token *token, enum aws_retry_error_type error_type, aws_retry_strategy_on_retry_ready_fn *retry_ready, void *user_data);
```
