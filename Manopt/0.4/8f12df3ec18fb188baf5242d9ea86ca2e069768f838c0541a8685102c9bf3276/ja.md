```
FrankWolfeCost{P,T}
```

[`Frank_Wolfe_method`](@ref)におけるオラクルサブ問題を表す構造体です。コスト関数は次のように定義されます。

$$
F(q) = ⟨X, \log_p q⟩
$$

値 `p` と `X` はこのファンクタ内に格納されており、[`FrankWolfeState`](@ref)内の反復と勾配への参照であるべきです。
