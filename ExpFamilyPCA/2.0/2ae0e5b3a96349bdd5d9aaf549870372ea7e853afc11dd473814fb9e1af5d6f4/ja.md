```
NegativeDomain(; metaprogramming::Bool = true, μ::Real = 1, ϵ::Real = eps(), low::Real = -1e10, high::Real = 1e10, tol::Real = 1e-10, maxiter::Real = 1e6)
```

負の領域での最適化のために構成された`Options`のインスタンスを返します。残りの設定は`Options`から保持しつつ、`A`と`V`パラメータのデフォルトを設定します。

# 特定の設定

  * `A_init_value = -1`: `A`を負の値で初期化します。
  * `A_upper = -1e-4`: `A`の上限は小さな負の値に制約されています。
  * `V_init_value = 1`: `V`を正の値で初期化します。
  * `V_lower = 1e-4`: `V`の下限は小さな正の値に制約されています。

他のフィールドは`Options`構造体から継承されます。
