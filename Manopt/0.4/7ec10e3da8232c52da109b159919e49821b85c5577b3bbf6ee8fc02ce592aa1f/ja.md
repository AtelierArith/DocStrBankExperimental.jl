```
FrankWolfeGradient{P,T}
```

[`Frank_Wolfe_method`](@ref)におけるオラクルサブ問題の勾配を表す構造体であり、与えられた点 `p` と接ベクトル `X` に対して、関数は次のように定義されます。

$$
F(q) = ⟨X, \log_p q⟩
$$

その勾配は `adjoint_differential_log_argument` を使用して簡単に計算できます。

値 `p` と `X` はこのファンクタ内に格納されており、[`FrankWolfeState`](@ref) 内の反復と勾配への参照であるべきです。
