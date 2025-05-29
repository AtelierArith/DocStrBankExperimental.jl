```
compose(op1::T, op2::T, modτ::Bool=true) where T<:SymOperation
```

2つの対称操作 `op1` $= \{W₁|w₁\}$ と `op2` $= \{W₂|w₂\}$ を合成則（Seitz表記）を用いて合成します。

$$
\{W₁|w₁\}\{W₂|w₂\} = \{W₁W₂|w₁+W₁w₂\}
$$

デフォルトでは、$\{W₁W₂|w₁+W₁w₂\}$ の翻訳部分は範囲 $[0,1[$ に減少され、すなわち 1 で計算されます。これはブールフラグ `modτ` によってオフ（またはオン）に切り替えることができます（デフォルトでは有効、すなわち `true`）。別の `SymOperation` を返します。

乗算演算子 `*` は `SymOperation` に対してオーバーロードされており、`op1 * op2 = compose(op1, op2, modτ=true)` のように `compose` を呼び出します。
