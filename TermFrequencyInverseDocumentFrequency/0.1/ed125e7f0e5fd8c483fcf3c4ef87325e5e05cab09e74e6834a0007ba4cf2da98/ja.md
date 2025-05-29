```
TermMatrix(corpus, vocab; pattern=r"\w\w+\b")
TermMatrix(matrix, features)
```

コーパスのnwords × ndocumentsの用語行列を計算します。各列は文書に対応し、各行は各文書における特定の用語の出現回数に対応します。

`tm.matrix` => 用語行列の疎行列表現。

`tm.features` => 用語を行番号にマッピングする辞書。
