```
iterated_integrals(W::Real, q_12::Real, h::Real, eps::Real; ito_correction=true, kwargs...)
```

スカラーQ-ウィーナー過程において、(スカラー)共分散Qを持つ場合、積分は明示的に計算できます。$\int_0^h\int_0^sdW(t)dW(s) = \frac{1}{2}W(h)^2 - \frac{1}{2}hQ$。

多次元の場合と同様に、パラメータ`q_12`は共分散の平方根を示します。

パラメータ`eps`（およびすべての追加キーワード引数）は影響を与えませんが、多次元バージョンと同じインターフェースを提供するために利用可能です。
