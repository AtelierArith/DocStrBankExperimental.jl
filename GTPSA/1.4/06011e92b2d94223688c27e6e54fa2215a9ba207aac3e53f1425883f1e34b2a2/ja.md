```
params(use::Union{Descriptor,TPS}=GTPSA.desc_current)
```

指定された `use` による `Descriptor` のパラメータに対応する `TPS` のベクトルを返します。デフォルト値は `GTPSA.desc_current` です。

### 入力

  * `use` – （オプション）使用する `Descriptor` を指定します。デフォルトは `GTPSA.desc_current` です。

### 出力

  * `x`   – 各パラメータに対応する単位 `TPS{Float64}` を含む `Vector`
