```
respond!(actr, task, key, args...; kwargs...)
```

ユーザー定義の `press_key!` 関数を使用してモーター応答を実行し、モジュールの状態を busy = false に設定します。

# 引数

  * `actr`: ACT-R モデルオブジェクト
  * `task`: `AbstractTask` のサブタイプであるタスク
  * `key`: 応答キーを表す文字列
