`mask(options; index, key)`

`options`の`index`-番目の要素のみを表示します。`options`が`AbstractDict`の場合、表示するオプションを`key`を使って指定することができます。`options`は`Observable`である可能性があり、その場合`mask`は自動的に更新されます。選択されたオプションを持たない場合は、`index=0`または`key = nothing`を使用します。

## 例

```julia
wdg = mask(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), index = 1)
wdg = mask(OrderedDict("plot" => plot(rand(10)), "scatter" => scatter(rand(10))), key = "plot")
```

`options`はウィジェットから直接変更することができることに注意してください：

```julia
wdg[:options][] = ["c", "d", "e"]
```
