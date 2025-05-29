```
transfer(f::T, sdof::Oscillator) where {T<:Real}
```

単自由度（SDOF）システムの伝達関数のモジュラスを計算します。

伝達関数は次のように定義されます：

$$
|H(f,f_n,\zeta_n)| = \frac{1}{\sqrt{ \left(1 - \beta^2 \right)^2 + \left(2\zeta_n\beta\right)^2 }}
$$

ここで、$\beta$は$f/f_n$で定義される調整比です。

# 例

```julia-repl
    f = 2.0
    sdof = Oscillator(1.0, 0.05)
    Hf = transfer(f, sdof)
```

参照： [`squared_transfer`](@ref)
