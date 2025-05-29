```
parameter_values(valp)
parameter_values(valp, i)
```

`valp`の各パラメータの値を含むインデックス可能なコレクションを返します。この関数の2引数バージョンは、インデックス`i`のパラメータ値を返します。この2引数バージョンの関数は、デフォルトで`parameter_values(valp)[i]`を返します。

この関数が`AbstractArray`または`Tuple`で呼び出されると、同じ配列/タプルを返します。
