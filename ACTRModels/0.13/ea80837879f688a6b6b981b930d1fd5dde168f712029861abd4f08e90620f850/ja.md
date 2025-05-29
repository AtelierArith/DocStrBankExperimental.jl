```
blend_chunks(actr, blended_slots, cur_time; request...)
```

取得リクエストに基づいてチャンクのブレンド値を計算します。値は `blended_slots` で指定されたスロットにわたってブレンドされます。現在、ブレンドは数値スロット値のみに対応しています。

# 引数

  * `actr`: `ACTR` モデルオブジェクト
  * `blended_slots`: スロット値がブレンドされるスロットのセット
  * `cur_time`: 現在のシミュレーション時間

# キーワード

  * `request...`: 取得リクエストのためのオプションキーワード
