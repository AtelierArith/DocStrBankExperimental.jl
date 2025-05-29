```
iterated_integrals(W::Real, h::Real, eps::Real=0.0; ito_correction=true, kwargs...)
```

スカラーのブラウン運動の場合、積分は明示的に計算できます：$\int_0^h\int_0^sdW(t)dW(s) = \frac{1}{2}W(h)^2 - \frac{1}{2}h$。

パラメータ `eps`（およびすべての追加のキーワード引数）は影響を与えませんが、多次元バージョンと同じインターフェースを提供するために利用可能です。
