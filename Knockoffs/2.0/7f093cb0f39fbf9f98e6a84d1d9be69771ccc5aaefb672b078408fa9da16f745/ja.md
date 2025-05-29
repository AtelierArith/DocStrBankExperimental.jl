```
solve_sdp_ccd(Σ::AbstractMatrix)
```

固定-Xおよびモデル-XノックオフのためのSDP問題を、相関行列Σを用いて座標降下法で解きます。ユーザーはこの関数の代わりに`solve_s`を呼び出すべきです。

# 参考文献

Askari et al. (2020)による「FANOK: Knockoffs in Linear Time」のアルゴリズム2.2。
