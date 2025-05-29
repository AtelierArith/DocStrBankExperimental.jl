```
span(interval::AbstractInterval) -> Any
```

上端点と下端点の間の差。制約のある区間では非負の値を返しますが、いずれかの端点が無制約の区間では `ArgumentError` をスローします。

例外を捕捉する必要がないように、次のパターンを使用します：

```julia
Intervals.isbounded(interval) ? span(interval) : infinity
```

ここで `infinity` は、無制約または無限のスパンを表すために使用したい値を表す変数です。
