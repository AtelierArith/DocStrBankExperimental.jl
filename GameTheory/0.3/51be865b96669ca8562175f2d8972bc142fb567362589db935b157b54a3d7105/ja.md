```
support_enumeration_task(c, g)
```

タスクバージョンの `support_enumeration`。

# 引数

  * `c::Channel`: サポート列挙タスクにバインドされるチャネル。
  * `g::NormalFormGame{2}`: 2人用のNormalFormGameインスタンス。

# 戻り値

  * `::Task`: ナッシュ均衡を生成するための実行可能なタスク。
