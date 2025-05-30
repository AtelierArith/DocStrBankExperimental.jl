```
interp1d(x, y, scheme::Symbol=:linear)
```

一次元曲線補間は、スキーム `[:constant, :linear, :quadratic, :cubic, :pchip, :lagrange]` を使用します。

注意：この補間方法は外挿を行います。
