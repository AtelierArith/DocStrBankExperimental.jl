```
start_task(start, sv, cb=nothing; 
           timeout::Real=5.0, pollint::Real=0.1)
```

`start`の動作を持つタスクを生成し、スーパーバイザー`sv`にそれを監視させます（再起動戦略は`:transient`）そしてその参照を返します。

# パラメータ

  * `start`: 呼び出し可能なオブジェクトである必要があります（引数なし）、
  * `sv`: スーパーバイザーのリンクまたは登録名、
  * `cb=nothing`: 再起動のためのコールバック（呼び出し可能なオブジェクトで、`Task`を返す必要があります）；`cb=nothing`の場合、タスクはその`start`関数で再起動されます、
  * `timeout::Real=5.0`: タスクが監視されるべき時間[秒]、
  * `pollint::Real=0.1`: ポーリング間隔[秒]。
