```
run(queue::Vector{Sim})
run(f::Function, queue::Vector{Sim})
```

キュー内の `Sim` オブジェクトを単一のプロセスで実行し、結果をデータフレームとして返します。

詳細については `run_parallel` を参照してください。
