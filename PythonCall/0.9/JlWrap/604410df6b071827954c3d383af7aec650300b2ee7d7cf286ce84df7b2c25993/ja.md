```
pystaticmethod(f; ...)
```

呼び出し可能な `f` を Python の静的メソッドに変換します。

`f` が Python オブジェクトでない場合（例えば、`f` が `Function` の場合）、それは [`pyfunc`](@ref PythonCall.pyfunc) を使って Python オブジェクトに変換されます。特に、`f` に渡される引数は常に `Py` 型です。任意のキーワード引数は `pyfunc` に渡されます。
