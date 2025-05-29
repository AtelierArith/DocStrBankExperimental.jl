```
LangJulia(overwrite_input=true,inline=true,alloc_function,only_overwrite=false)
```

Julia言語でのコード生成で、入力の上書きをオプションで行います。パラメータ `alloc_function` は三つのパラメータを持つ関数 `alloc_function(k)` で、ここで `k` はメモリスロット（デフォルトは `alloc_function(k)=similar(A,T)` です）。`only_overwrite` は、上書き関数 `f!` に実際のコードが含まれている場合に `f` を作成するかどうかを指定します。
