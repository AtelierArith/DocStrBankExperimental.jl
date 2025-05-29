```
WallTimeInterval(interval; start_time = time_ns() * 1e-9)
```

シミュレーションが実行されている間、"壁時間" の `interval` ごとに定期的な出力または診断評価をスケジュールする呼び出し可能な `WallTimeInterval` を返します。単位は秒です。

"壁時間" とは、実際の時計が壁に掛かっている場合のように、実際の現実世界の時間を秒単位で表したものです。

キーワード引数 `start_time` を使用して、`WallTimeInterval` が構築される瞬間以外の開始壁時間を指定することができます。
