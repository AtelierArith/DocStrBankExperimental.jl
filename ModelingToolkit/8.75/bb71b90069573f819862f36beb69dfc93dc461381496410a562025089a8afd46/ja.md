```julia
structural_simplify(sys; ...)
structural_simplify(sys, io; simplify, kwargs...)

```

システム内の代数方程式を構造的に簡素化し、観測された方程式のトポロジカルソートを計算します。`simplify=true` の場合、`simplify` 関数が切断プロセス中に適用されます。また、切断中の係数タイプを制限する `allow_symbolic=false` と `allow_parameter=true` の kwargs を受け取ります。

オプションの引数 `io` はタプル `(inputs, outputs)` を取ることができます。これにより、すべての `inputs` がパラメータに変換され、接続されていないことが許可されます。すなわち、簡素化は `n_states = n_equations - n_inputs` のモデルを許可します。
