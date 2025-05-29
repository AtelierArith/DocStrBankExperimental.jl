```
compose!(m::TPSAMap, m2::TPSAMap, m1::TPSAMap; dospin::Bool=true, work_prom::Union{Nothing,Tuple{Vararg{Vector{<:ComplexTPS64}}}}=prep_comp_work_prom(m,m2,m1))
```

インプレース `TPSAMap` 合成は `m = m2 ∘ m1` を計算し、`m1` のスカラー部分を含みます。

エイリアシング `m === m2` は許可されていますが、`m === m1` は許可されていません。`m2 === m1` は問題ありません。宛先マップ `m` は適切に設定されている必要があり（必要に応じて正しい型が昇格され）、`m.x[1:nv]`（およびスピンがある場合は `m.Q`）には割り当てられた TPS が含まれている必要があります。

`dospin` が `true` の場合、マップのクォータニオン部分も合成されます。デフォルトは `true` です。

`work_prom` に関する情報は `compose_it!` のドキュメントを参照してください。

### キーワード引数

  * `dospin` – 結合にクォータニオンを含めるかどうかを指定します。デフォルトは `true`
  * `work_prom` – 暗黙の昇格がある場合に割り当てられた `ComplexTPS64` の一時ベクター。詳細については `compose_it!` のドキュメントを参照してください。デフォルトは `prep_comp_work_prom(m, m2, m1)` の出力です。
