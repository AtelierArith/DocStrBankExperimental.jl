```
HasDimNames(img) -> HasDimNames{::Bool}
```

`HasDimNames`を返し、`x`に名前付き次元があるかどうかを示します。`HasDimNames{true}()`を返す型は、各次元のシンボルのタプルを返す`names`メソッドも持っている必要があります。
