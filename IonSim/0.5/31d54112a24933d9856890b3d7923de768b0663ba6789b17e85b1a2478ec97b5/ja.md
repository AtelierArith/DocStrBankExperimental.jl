```
thermalstate(v::VibrationalMode, n̄::Real; method="truncated")
```

$$
⟨a^†a⟩ ≈ n̄
$$

を持つ熱密度行列を返します。注意：有限次元のヒルベルト空間を扱っているため、近似的です。

`method` は `"truncated"`（デフォルト）または `"analytic"` のいずれかに設定できます。前者の場合、熱密度行列は次の式に従って生成されます：$ρ_{th} = exp(-νa^†a/T) / Tr [exp(-νa^†a/T)]$。後者の場合、無限次元のヒルベルト空間を仮定した解析的な式が使用されます：$[ρ_{th}]_{ij} = δ_{ij} \frac{nⁱ}{(n+1)^{i+1}}.$
