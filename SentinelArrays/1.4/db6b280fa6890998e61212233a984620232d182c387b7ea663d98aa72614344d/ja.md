```
ChainedVector(arrays::Vector{<:AbstractVector})
```

同種の型の `AbstractVector` の `Vector` の `ChainedVector` を作成します。入力ベクトルの「チェーン」は、単一の長いベクトルとして扱われます。典型的な可変操作のフルセットがサポートされています（例：`push!`、`append!` など）。

実装の詳細として、単一要素に対する可変操作（例：`setindex!`、`push!`）はインプレースで動作するか、既存のチェーン配列を変更しますが、`append!`/`prepend!` は、受信した配列を既存のチェーン配列に「チェーン」するように最適化されています。
