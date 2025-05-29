```
responding!(actr, task, key, args...; kwargs...)
```

宣言的モーターモジュールをビジー状態に設定し、キー入力を実行するための新しいイベントを登録します。

# 引数

  * `actr`: ACT-Rモデルオブジェクト
  * `task`: `AbstractTask`のサブタイプであるタスク
  * `key`: 応答キーを表す文字列
