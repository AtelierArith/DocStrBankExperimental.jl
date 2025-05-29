```
execute!(job::AbstractJob, exec::Executor)
```

指定された `AbstractJob` を `Executor` に関連付けて実行します。

この関数は、`job` が成功したかどうかを確認します。成功している場合は、すぐに停止します。そうでない場合は、`exec.delay` の間スリープし、その後 `job` を実行します。`exec.maxattempts` が $1$ より大きい場合は、残りの試行をループし、`exec.interval` の間スリープし、`job` を実行し、各ループで待機します。
