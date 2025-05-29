```
AbstractSemiring <: Number
```

[`セミリング`](https://en.wikipedia.org/wiki/Semiring) は、加算と乗算と呼ばれる2つの二項演算 + と ⋅ を備えた集合 R であり、次の条件を満たします：

  * (R, +) は、0 と呼ばれる単位元を持つモノイドである；
  * (R, ⋅) は、1 と呼ばれる単位元を持つモノイドである；
  * 加算は可換である；
  * 加法単位元 0 による乗算は消去する；
  * 乗算は加算に対して左および右に分配される；
  * 明示的に述べると、(R, +) は可換モノイドである。

[`トロピカル数`](https://en.wikipedia.org/wiki/Tropical_geometry) は、次のように記述されるセミリング代数の集合です：

  * (R, +, ⋅, 0, 1)。

ここで R は集合、+ と ⋅ は演算、0 と 1 はそれぞれの単位元です。

このパッケージでは、次のトロピカル代数が実装されています：

  * TropicalAndOr, ([T, F], or, and, false, true);
  * Tropical (TropicalMaxPlus), (ℝ, max, +, -Inf, 0);
  * TropicalMinPlus, (ℝ, min, +, Inf, 0);
  * TropicalMaxMul, (ℝ⁺, max, ⋅, 0, 1)。

私たちは、[`TropicalGEMM`](https://github.com/TensorBFS/TropicalGEMM.jl/) と [`CuTropicalGEMM`](https://github.com/ArrogantGao/CuTropicalGEMM.jl/) において、高速なトロピカル行列乗算を実装しました。
