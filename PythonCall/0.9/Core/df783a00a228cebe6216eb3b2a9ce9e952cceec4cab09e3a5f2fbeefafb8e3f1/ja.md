```
pydict(x)
pydict(; x...)
```

`x`をPythonの`dict`に変換します。2番目の形式では、キーは文字列です。

`x`がPythonオブジェクトである場合、これはPythonの`dict(x)`に相当します。それ以外の場合、`x`はキーと値のペアを反復処理する必要があります。
