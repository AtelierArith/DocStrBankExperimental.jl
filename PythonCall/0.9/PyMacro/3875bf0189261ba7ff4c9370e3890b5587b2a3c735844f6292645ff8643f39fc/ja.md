```
@py expr
```

与えられた式をPython的なセマンティクスを使用して評価します。

例えば：

  * `f(x, y)` は `pycall(f, x, y)` に翻訳されます。
  * `x + y` は `pyadd(x, y)` に翻訳されます。
  * `x === y` は `pyis(x, y)` に翻訳されます（Pythonでは `x is y`）。
  * `x.foo` は `pygetattr(x, "foo")` に翻訳されます。
  * `import x: f as g` は `g = pyimport("x" => "f")` に翻訳されます（Pythonでは `from x import f as g`）。

`begin`、`if`、`while`、`for` などの複合文もサポートされています。

詳細についてはオンラインドキュメントを参照してください。

!!! 警告     このマクロは実験的です。将来のリリースで変更されるか、削除される可能性があります。
