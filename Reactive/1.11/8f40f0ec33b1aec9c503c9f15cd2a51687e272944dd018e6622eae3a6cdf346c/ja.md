```
remoterefs, results = remote_map(procid, f, init, input...;typ=typeof(init), onerror=Reactive.print_error)
```

プロセス `procid` で新しいタスクを生成し、入力信号が更新されると関数を実行します。リモート参照の信号と、結果とともに非同期に更新される `results` 信号を返します。`init` は `results` のデフォルト値として使用されます。`onerror` はエラーが発生したときに呼び出されるコールバックで、デフォルトではエラーを stderr に印刷するコールバックに設定されています。これは `push!` の `onerror` 引数と同じですが、生成されたタスク内で実行されます。
