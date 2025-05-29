```
shifted(h, x)
shifted(h, x, Δ, ρ)
```

近接可能関数または別のシフトされた近接可能関数からシフトされた近接可能関数を構築します。

`h` が `ProximableFunction`（シフトされた近接可能関数を含む）の場合、形式 `shifted(h, x)` は `ψ` という `ShiftedProximableFunction` を返します。ここで `ψ(s) == h(x + s)` です。続いて、`ψ` に対して `prox` を呼び出すことができます。最初の形式は `h` が `ShiftedProximableFunction` の場合に適用され、すでにシフトされた近接可能関数をシフトするために使用できます。

形式 `shifted(h, x, Δ, ρ)` は `ψ` という `ShiftedProximableFunction` を返します。ここで `ψ(s) == h(x + s) + Ind({‖s‖ ≤ Δ})` であり、`Ind(.)` は集合の指示関数を表します。この場合、半径 `Δ` のボールの指示関数です。ノルムは `ρ` によって定義されます。

### 引数

  * `h::ProximableFunction`（シフトされた近接可能関数を含む）
  * `x::AbstractVector`
  * `Δ::Real`
  * `ρ::ProximableFunction`.

`h` と `ρ` の特定の組み合わせのみがサポートされています。これは、近接演算子の解析形式が知られているものです。

`h` が以前の `shifted()` の呼び出しから得られたシフトされた近接可能関数である場合、サポートされるのは `shifted(h, x)` の形式のみです。該当する場合、結果として得られるシフトされた近接可能関数は `h` と同じ `Δ` と `ρ` に関連付けられます。

詳細については、ProximalOperators.jl のドキュメントを参照してください。
