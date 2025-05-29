```
eachobsparallel(data; useprimary = false, buffered = true)
```

データコンテナ `data` のための並列データイテレータ。`useprimary` が `false` の場合、最初のスレッドを除くすべての利用可能なスレッドでデータをロードします。

`buffered` が `true` の場合、`getobs!` を使用してサンプルをインプレースでロードします。

`MLDataPattern.eachobs` も参照してください。

!!! warning "順序"
    `eachobsparallel` はサンプルが正しい順序で返されることを保証しません。

