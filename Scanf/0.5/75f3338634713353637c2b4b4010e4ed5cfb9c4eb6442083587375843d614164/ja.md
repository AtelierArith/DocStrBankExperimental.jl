```
Scanf.scanf(b::String, f::Scanf.Format, args...)
Scanf.scanf([io::IO,] f::Scanf.Format, args...)
```

提供された文字列に Scanf フォーマットオブジェクト `f` を適用する（1 番目のメソッド）、または `io` オブジェクトから直接スキャンする（2 番目のメソッド）。C の `scanf` サポートの詳細については [`@scanf`](@ref) を参照してください。`io` はデフォルトで `stdin` です。args は出力データの型とデフォルト値を決定します。

割り当てられた引数の数と、続いて割り当てられた出力データを返します。
