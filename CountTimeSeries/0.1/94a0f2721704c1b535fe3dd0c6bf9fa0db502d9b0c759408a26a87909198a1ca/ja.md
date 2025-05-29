```
HQIC(results, dropfirst)
```

ハンナン-クイン情報基準を計算します。

  * `results`: カウントデータモデルのフィッティングからの結果。
  * `dropfirst`: 計算から最初の観測値を除外するために使用できます。

# 例

```julia-repl
HQIC(res1, 2) # res1: INARCH(1) フィットからの結果
HQIC(res2)    # res2: INARCH(2) フィットからの結果
```
