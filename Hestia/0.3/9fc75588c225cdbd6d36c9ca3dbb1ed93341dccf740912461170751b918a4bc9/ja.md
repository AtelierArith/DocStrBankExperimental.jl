```
Emission  <: AbstractEmission
```

タイプ Emission は (対流) 熱伝達と熱放射の係数を含みます。

$$
\Phi = -h ~ (\theta - \theta_{amb}) - \sigma ~ [\varepsilon_{1} ~ \theta^4 - \varepsilon_{2} ~ \theta_{amb}^4)]
$$

コンストラクタ `Emission(h, θamb, ε₁, ε₂, θext)` は放射率 `ε₁` と `ε₂` を期待し、これらは区間 [0,1] にある必要があります。ステファン・ボルツマン定数は内部に保存されています: `σ = 5.6703744191844294e-8`。

### 要素

`h` : 熱伝達係数

`θamb` : 周囲温度

`ε₁` : 主な物体の放射率

`ε₂` : 外部第二体の放射率

`θext` : 外部第二体の温度
