```
genus(T::TorQuadModule, signature_pair::Tuple{Int, Int};
                        parity::RationalUnion = modulus_quadratic_form(T))
                                                                -> ZZGenus
```

与えられた `signature_pair` と与えられた `parity` を持つ、`T` の双線形形式を持つ整数格子の属を返します。

引数 `parity` は次のいずれかです：奇数格子の属の場合は `parity == 1`、偶数格子の場合は `parity == 2`。デフォルトでは、`parity` は `T` の二次形式のパリティとして設定されます。

そのような属が存在しない場合は、エラーを発生させます。

# 参考文献

[Nik79](@cite) 補題 1.9.4 および 1.16.3。
