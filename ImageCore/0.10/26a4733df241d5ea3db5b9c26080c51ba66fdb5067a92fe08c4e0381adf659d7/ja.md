```
HasDimNames(img) -> HasDimNames{::Bool}
```

`HasDimNames`トレイトを返し、`x`が名前付き次元を持っているかどうかを示します。`HasDimNames{true}()`を返す型は、各次元のシンボルのタプルを返す`names`メソッドも持っている必要があります。
