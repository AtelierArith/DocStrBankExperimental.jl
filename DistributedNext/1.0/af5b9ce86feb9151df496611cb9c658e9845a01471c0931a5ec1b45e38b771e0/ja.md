```
clear!(syms, pids=workers(); mod=Main)
```

モジュール内のグローバルバインディングを `nothing` に初期化することでクリアします。 `syms` は [`Symbol`](@ref) 型であるか、`Symbol` のコレクションである必要があります。 `pids` と `mod` は、グローバル変数を再初期化するプロセスとモジュールを特定します。 `mod` の下で定義されていると見なされる名前のみがクリアされます。

グローバル定数をクリアするよう要求された場合、例外が発生します。
