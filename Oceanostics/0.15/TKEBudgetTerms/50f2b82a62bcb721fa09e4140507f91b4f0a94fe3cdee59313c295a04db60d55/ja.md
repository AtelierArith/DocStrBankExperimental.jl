```julia
IsotropicKineticEnergyDissipationRate(
    model;
    U,
    V,
    W,
    location
)

```

粘性散逸率を計算します。これは次のように定義されます。

```
ε = 2 ν SᵢⱼSᵢⱼ,
```

ここで、Sᵢⱼはひずみ率テンソルであり、各方向に対してν（渦または非渦）が同じである等方的乱流閉じ込めを持つ流体に対して適用されます。
