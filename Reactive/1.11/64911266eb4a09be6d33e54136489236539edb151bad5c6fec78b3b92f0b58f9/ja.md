```
filterwhen(switch::Signal{Bool}, default, input)
```

`switch` が true のときのみ `input` への更新を保持します。

最初に `switch` が false の場合、指定されたデフォルト値が使用されます。
