```
load_adaptive_time_integrator!(integrator, restart_file::AbstractString)
```

エラーに基づくステップサイズ制御を持つ時間積分器のコンテキスト情報を `restart_file` に保存されたものから読み込みます。
