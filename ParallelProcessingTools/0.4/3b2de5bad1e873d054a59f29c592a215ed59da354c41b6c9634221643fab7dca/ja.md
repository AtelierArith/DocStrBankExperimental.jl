```
@mt_out_of_order begin expr... end
```

`begin expr... end`内のすべてのトップレベルの式を並列のマルチスレッドタスクで実行します。

例:

```@mt*out*of_order begin     a = foo()     bar()     c = baz() end

は、`a = foo()`、`bar()`、および`c = baz()`を並列で任意の順序で実行し、代入の結果は外部スコープに現れます。
```
