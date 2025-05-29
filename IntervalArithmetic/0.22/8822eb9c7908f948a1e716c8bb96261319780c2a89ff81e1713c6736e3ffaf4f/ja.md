```
Domain{LeftBound, RightBound}(lo, hi)
```

関数の定義域。

`LeftBound` と `RightBound` はシンボルであり、それぞれ `:closed` または `:open` で、対応する端点が（それぞれ）定義域に含まれるかどうかを決定します。

もし `hi > lo` の場合、定義域は空であると見なされます。
