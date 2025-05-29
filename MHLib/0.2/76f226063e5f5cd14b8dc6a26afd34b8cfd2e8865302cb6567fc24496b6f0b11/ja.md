```
destroy!(sol::OneMaxSolution, k::Int, result::Result)
```

`MHMethod` は、`shaking!` を呼び出すことによって解 `sol` の `k` ビットを破壊します。

これは OneMax 問題にとって本当に意味のある破壊操作ではないことに注意してください。これは、この問題に (A)LNS を使用できるようにするためのテスト目的のものです。
