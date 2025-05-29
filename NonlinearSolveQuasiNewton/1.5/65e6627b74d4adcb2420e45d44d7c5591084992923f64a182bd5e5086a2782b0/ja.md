```
Klement(;
    max_resets = 100, linsolve = nothing, linesearch = nothing,
    alpha = nothing, init_jacobian::Val = Val(:identity),
    autodiff = nothing
)
```

`Klement` [klement2014using](@citep) の実装で、ラインサーチ、前処理、およびカスタマイズ可能な線形解法を備えています。ほとんどの問題には [`Broyden`](@ref) を使用することをお勧めします。

### キーワード引数

  * `max_resets`: 実行する最大リセット数。デフォルトは `100` です。
  * `alpha`: `init_jacobian` が `Val(:identity)` に設定されている場合、初期ヤコビアンの逆行列は `αI` に設定されます。デフォルトは `1` です。`nothing` に設定することもでき、これは `α = max(norm(u), 1) / (2 * norm(fu))` を意味します。
  * `init_jacobian`: ヤコビアンを初期化するために使用する方法。デフォルトは `Val(:identity)` です。選択肢には以下が含まれます：

      * `Val(:identity)`: 単位行列。
      * `Val(:true_jacobian)`: 真のヤコビアン。私たちのテストでは、これはあまり安定していないことが示唆されています。代わりに `Val(:true_jacobian)` を使用した `Broyden` を使用すると、より速く、より信頼性の高い収束が得られます。
      * `Val(:true_jacobian_diagonal)`: 真のヤコビアンの対角成分。これは微分可能な問題に対して良い選択です。
