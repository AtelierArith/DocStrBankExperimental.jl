**グリッド上で**

```
gmpe_simidorikawa1999(
    eq::Earthquake,config::Params_simidorikawa1999,
    grid::Array{Point_vs30};
    min_val::Number
)
```

ここで `min_val=0` がデフォルトです。

出力は、`pga > min_val` に基づく入力グリッドのポイントを持つ 1 次元 `Array{Point_pga_out}` になります（pga は重力加速度のパーセント (%g) を ggg.gg に丸めたものです）。

**グリッドなしで**

```
gmpe_simidorikawa1999(
    eq::Earthquake,
    config::Params_simidorikawa1999;
    VS30::Number=350,
    distance::Int64=1000
)
```

ここで `VS30=30` [m/s^2]、`distance=1000` [km] がデフォルトです。

出力は、`1:distance` の `pga` 値を持つ 1 次元 `Array{Float64,1}` になります（これは重力加速度 (g) のパーセントを ggg.gg に丸めたものです）。

**例:**

```
gmpe_simidorikawa1999(
    eq,config_simidorikawa1999_interplate,grid
) # グリッド上でのPGA

gmpe_simidorikawa1999(
    eq,config_simidorikawa1999_intraplate
) # 入力グリッドなしでのPGA
```

**モデルパラメータ**

`examples/si-midorikawa-1999.conf` を参照してください。
