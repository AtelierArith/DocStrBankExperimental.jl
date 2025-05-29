```
function alloc_segbuf(domain_type=Float64, range_type=Float64, error_type=Float64; size=1)
```

このヘルパーは、与えられた `domain_type` に対して `quadgk(...)` 呼び出しのためのセグメントバッファを割り当てます。`domain_type` は積分限界の型と同じであり、`range_type` は積分される関数の範囲、`error_type` は `quadgk(...)` に与えられた `norm` によって返される型であり、与えられた `size` から始まります。このバッファは、複数の互換性のある `quadgk(...)` 呼び出しにわたって再利用でき、繰り返しの割り当てを避けることができます。

あるいは、最初の `quadgk(...)` 呼び出しを `quadgk_segbuf(...)` の呼び出しに置き換えることができ、これにより最初の積分から計算されたセグメントバッファが返されます。これにより、積分関数が変数である場合に明らかでないかもしれない `domain_type` などを考える手間が省けます。
