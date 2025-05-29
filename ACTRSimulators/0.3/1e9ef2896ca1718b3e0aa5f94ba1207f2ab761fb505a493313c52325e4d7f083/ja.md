```
run!(actr, task::AbstractTask, until=Inf)
```

ACT-Rモデルをシミュレートします

# 引数

  * `models`: ACT-Rモデルオブジェクトの辞書
  * `task`: `AbstractTask`のサブタイプであるタスク
  * `until=Inf`: 手動で早期に終了しない限り、指定された終了時間
