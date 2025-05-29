```
is_genus(T::TorQuadModule, signature_pair::Tuple{Int, Int};
                           parity::RationalUnion = modulus_quadratic_form(T)) -> Bool
```

整数格が存在するかどうかを返します。その格の判別形式は `T` の双線形形式を持ち、署名は `signature_pair` と一致し、パリティは `parity` です。

引数 `parity` は次のいずれかです：奇数格の属に対しては `parity == 1`、偶数格に対しては `parity == 2` です。デフォルトでは、`parity` は `T` の二次形式のパリティとして設定されています。
