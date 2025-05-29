```
startboard960(i=nothing)
```

`Board`オブジェクトをチェス960の開始位置で返します。

オプションのパラメータ`i` – 0..959の範囲の整数 – は、[こちら](https://en.wikipedia.org/wiki/Fischer_random_chess_numbering_scheme)で説明されているインデックス方式を使用して特定のチェス960の位置を選択するために使用されます。このパラメータが省略されると、関数はランダムな位置を選択します。
