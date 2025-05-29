```
ProcessResultCache(params::AbstractImageReconstructionParameters; maxsize = 1, kwargs...)
```

`process` メソッドの結果のためのサイズ `maxsize` のキャッシュ。キャッシュは `process` 関数の入力の `hash` に基づいています。キャッシュは同じプランから構築されたすべてのアルゴリズム間で共有されます。キャッシュは基盤となるパラメータのプロパティに対して透過的です。キャッシュは `empty!` を呼び出すことで無効にすることができます。
