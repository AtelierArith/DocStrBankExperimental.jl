`baseX(W::ComplexReflectionGroup)`

は、行列の行として、`W` が作用する空間 `V` の特定の基底を返します：最初の `semisimplerank(W)` 行は、根格子の基底の `V` の基底上の座標を含み（`simpleroots(W)[independent_roots(W)]` によって与えられます）、最後の `rank(W)-semisimplerank(W)` 行は、コルートの直交に関する同じものを含みます。

`W` が冗長群のルートデータを表すとき、最初の行は `simpleroots(W)` と同じです。
