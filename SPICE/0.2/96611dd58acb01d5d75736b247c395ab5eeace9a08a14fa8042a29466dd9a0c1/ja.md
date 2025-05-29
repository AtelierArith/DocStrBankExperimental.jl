```
ncpos(str, chars, start)
```

文字列内で、指定された位置から前方に検索し、コレクションに属さない最初の文字の出現を見つけます。

### 引数

  * `str`: 文字列
  * `chars`: 文字のコレクション
  * `start`: `chars` に含まれない文字を探し始める位置

### 出力

`chars` のコレクションに含まれない `start` インデックス以降の `str` の最初の文字のインデックスを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ncpos_c.html)
