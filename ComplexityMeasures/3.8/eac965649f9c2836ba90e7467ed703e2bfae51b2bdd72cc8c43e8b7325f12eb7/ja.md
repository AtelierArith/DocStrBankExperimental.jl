```
StretchedExponential <: InformationMeasure
StretchedExponential(; η = 2.0, base = 2)
```

ストレッチ指数、またはアンテネオド-プラスティーノエントロピー [Anteneodo1999](@cite) は、[`information`](@ref) と共に使用されて計算されます。

$$
S_{\eta}(p) = \sum_{i = 1}^N
\Gamma \left( \dfrac{\eta + 1}{\eta}, - \log_{base}(p_i) \right) -
p_i \Gamma \left( \dfrac{\eta + 1}{\eta} \right),
$$

ここで、$\eta \geq 0$、$\Gamma(\cdot, \cdot)$ は上部不完全ガンマ関数、$\Gamma(\cdot) = \Gamma(\cdot, 0)$ はガンマ関数です。`η = 1.0` の場合、[`Shannon`](@ref) エントロピーに還元されます。

`StrechedExponential` の最大エントロピーは、不完全ガンマ関数を含むかなり複雑な表現です（ソースコードを参照）。
