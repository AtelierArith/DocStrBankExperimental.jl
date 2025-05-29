```
use_superancillaries!(val::Bool = true)
```

立方体およびPC-SAFTスーパアンシラリーを`saturation_pressure`の初期点として使用することを有効にします。`PCSAFT`の場合、臨界点計算のためのスーパアンシラリーの使用も有効になります。この関数は、現在のセッションで`EoSSuperancillaries.jl`がロードされている必要があります（`using EoSSuperancillaries`）。
