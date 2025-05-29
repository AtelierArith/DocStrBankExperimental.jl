```
primitivize(op::SymOperation, cntr::Char, modw::Bool=true) --> typeof(op)
```

対称操作 `op′` $≡ \{W'|w'\}$ を、従来の設定における入力対称操作 `op` $= \{W|w\}$ から変換して、原始的な設定で返します。操作 $\{W'|w'\}$ と $\{W|w\}$ は、変換 $\{P|p\}$ によって関連付けられています（[のセクション 1.5.2.3 を参照]（[^ITA6））:

$$
\{W'|w'\} = \{P|p\}⁻¹\{W|w\}\{P|p\}.
$$

ここで、$P$ と $p$ はそれぞれ基底変換行列と原点のシフトです。関連する変換 $\{P|p\}$ は、`cntr` によって提供される中心タイプから推測されます（[`Bravais.centering`](@ref) も参照）。

デフォルトでは、`op′` の平行移動部分、すなわち $w'$ は 1 で剰余を取られます（`modw = true`）。これを無効にするには、`modw = false` に設定します。

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th ed. (2016).
