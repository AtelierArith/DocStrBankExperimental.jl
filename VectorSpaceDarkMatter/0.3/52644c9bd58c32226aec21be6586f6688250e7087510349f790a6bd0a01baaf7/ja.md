```
GaussianF(c::Float64, uSph::Vector{Float64}, sigma::Float64)
```

ガウス関数のパラメータを含み、`uSph`はガウスの中心を示す球面ベクトルであり、`uSph = (u, theta, phi)`です。`sigma`は分散（「通常の」ガウスにおいては$\sqrt{2} \sigma$に等しい）です。`c`は全体の振幅です。`u`と`sigma`は同じ単位である必要があります。

`GaussianF`のインスタンス`g`は`g(uvec)`によって呼び出すことができ、`uvec = [u, theta, phi]`でガウスを評価します。
