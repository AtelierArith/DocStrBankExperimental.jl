```
ElectronicEntropy <: InformationMeasure
ElectronicEntropy(; h = Shannon(; base = 2), j = ShannonExtropy(; base = 2))
```

["電子エントロピー"](https://en.wikipedia.org/wiki/Electronic_entropy) 測定は、[Lad2015](@citet) において離散形式で定義されています。

$$
H_{EL}(p) = H_S(p) + J_S(P),
$$

ここで、$H_S(p)$ は [`Shannon`](@ref) エントロピーであり、$J_S(p)$ は確率ベクトル $p$ の [`ShannonExtropy`](@ref) エントロピーです。
