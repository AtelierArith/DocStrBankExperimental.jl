```
@symExpr(expr)
```

Symataは`expr`を評価し、その結果をJuliaの式に変換して周囲のコードに挿入します。これは、Symata式を評価することによって生成されたコードを挿入するためのJuliaマクロと同じように機能します。

以下は、Symataコードを評価し、その結果をJuliaに変換してJulia関数の本体として使用する例です。

```
julia> f1(z) = @symExpr Together(PolyLog(-1,z) + (1-z))
```
