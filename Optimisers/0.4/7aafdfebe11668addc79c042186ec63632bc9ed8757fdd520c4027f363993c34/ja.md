```
SignDecay(λ = 1e-3)
SignDecay(; [lambda])
```

$$
L_1
$$

正則化、別名 LASSO 回帰を実装します。他のルールと組み合わせて [`OptimiserChain`](@ref) の最初の変換として使用されます。

これは、勾配に `λ .* sign(x)` を追加することによって行われます。これは、損失に `λ * sum(abs, x) == λ * norm(x, 1)` を追加することと同等です。

$$
L_2
$$

正規化については [`WeightDecay`] も参照してください。これらは一緒に使用できます：`OptimiserChain(SignDecay(0.012), WeightDecay(0.034), Adam())` は、損失関数に `0.012 * norm(x, 1) + 0.017 * norm(x, 2)^2` を追加することと同等です。

# パラメータ

  * ペナルティ (`λ ≥ 0`): 正則化の強さを制御します。
