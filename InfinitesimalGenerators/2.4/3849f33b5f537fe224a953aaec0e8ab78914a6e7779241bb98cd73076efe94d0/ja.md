```
feynman_kac(𝕋, ts; f =  zeros(size(𝕋, 1)), ψ =  zeros(size(𝕋, 1)), v = zeros(size(𝕋, 1)), direction = :backward])
```

𝕋 は行列であり、ts は PDE を解くための時間のグリッドである必要があります。

direction = :backward の場合、PDE の解を返します: u(x, t[end]) = ψ(x) 0 = u*t + 𝕋u - v(x, t)u + f(x, t) または、同等に、積分形式で、 u(x, t) = E[∫*t^T e^{-∫*t^s v(x*u) du} f(x*s)ds + ∫*t^t e^{-∫*t^T v(x*u)du} ψ(x*T)|x*t = x] （表記は Feynman–Kac 公式に関するウィキペディアの記事からのものです）

direction = :forward の場合、PDE の解を返します: u(x, t[1]) = ψ(x) u*t = 𝕋u - v(x, t)u + f(x, t) または、同等に、積分形式で、 u(x, t) = E[∫*0^t e^{-∫*0^s v(x*u) du} f(x*s)ds + ∫*0^t e^{-∫*0^t v(x*u)du} ψ(x*t)|x*0 = x]

PDE は、暗黙的な時間ステップを用いたオイラー法で解かれます。
