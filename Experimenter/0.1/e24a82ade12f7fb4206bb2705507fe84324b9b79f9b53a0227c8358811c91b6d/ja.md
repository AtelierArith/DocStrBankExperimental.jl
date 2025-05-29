```
@execute experiment database [mode=SerialMode use_progress=false directory=pwd()]
```

グローバルスコープから実験を実行し、結果を`database`に保存し、すでに実行されたすべてのトライアルをスキップします。

# 引数:

mode: SerialMode、MultithreadedMode、またはDistributedModeを指定して、直列または並列で実行します。 use_progress: プログレスバーを表示します directory: 実行のために現在のプロセス（またはワーカープロセス）を変更するディレクトリ。
