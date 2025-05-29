```
spectra(x::Pair{I,C}, min_count::Integer = 0) where {I,C<:AbstractKmerCounter}
```

1次元のkmer頻度スペクトルを構築します。入力引数`x`として（入力データ => kmerカウンタ）のペアを使用します。spectra関数は、入力データからカウントを取得するためにkmerカウンタを使用し、その後スペクトルを計算します。

`min_count`を満たさないkmerカウントは除外されます。
