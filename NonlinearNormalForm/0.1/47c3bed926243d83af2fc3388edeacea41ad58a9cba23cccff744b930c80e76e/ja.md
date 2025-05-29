```julia
compose!(m::DAMap, m2::DAMap, m1::DAMap; keep*scalar::Bool=true, work*ref::Union{Nothing,Vector{<:Union{Float64,ComplexF64}}}=nothing, dospin::Bool=true, work*prom::Union{Nothing,Tuple{Vararg{Vector{<:ComplexTPS64}}}}=prep*comp*work*prom(m,m2,m1))

インプレース `DAMap` 合成は `m = m2 ∘ m1` を計算し、`m1` のスカラー部分を無視します。

`m === m2` のエイリアスは許可されていますが、`m === m1` は許可されていません。`m2 === m1` は問題ありません。宛先マップ `m` は適切に設定されている必要があり（必要に応じて正しい型が昇格され）、`m.x[1:nv]`（およびスピンがある場合は `m.Q`）には割り当てられた TPS が含まれている必要があります。

`keep_scalar` が `true` に設定されている場合、`m1` のスカラー部分が保持されます。この場合、一時的なベクトル `work_ref` を使用してスカラー部分を保存し、低レベルの `compose_it!` を呼び出す前に、合成後に `m1` に戻す必要があります。`work_ref` はオプションで提供することもできますし、この場合は内部で作成されます。デフォルトは `true` です。

`dospin` が `true` の場合、マップのクォータニオン部分も合成されます。デフォルトは `true` です。

`work_prom` に関する情報は `compose_it!` のドキュメントを参照してください。

### キーワード引数

  * `keep_scalar` – `m1` のスカラー部分を保持するか、捨てるかを指定します。`true` の場合、スカラー部分を保存するための一時的なベクトルを使用する必要があります。デフォルトは `true`
  * `work_ref` – `keep_scalar` が `true` の場合、このキーワード引数で一時的なベクトルを提供できます。`nothing` が提供された場合、一時的なベクトルは内部で作成されます。デフォルトは `nothing`
  * `dospin` – 連結にクォータニオンを含めるかどうかを指定します。デフォルトは `true`
  * `work_prom` – 暗黙の昇格がある場合の割り当てられた `ComplexTPS64` の一時的なベクトル。詳細については `compose_it!` のドキュメントを参照してください。デフォルトは `prep_comp_work_prom(m, m2, m1)` の出力です
```
