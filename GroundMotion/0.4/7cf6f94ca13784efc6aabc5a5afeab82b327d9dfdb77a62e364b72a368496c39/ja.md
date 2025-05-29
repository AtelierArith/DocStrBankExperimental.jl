**グリッド上で**

```
gmpe_as2008(
    eq::Earthquake,
    config_as2008::Params_as2008,
    grid::Array{Point_vs30};
    min_val::Number
)
```

ここで `min_val=0` がデフォルトです。

出力は、`pga > min_val` に基づく入力グリッドのポイントを持つ 1 次元 `Array{Point_pga_out}` になります（pga は重力の加速度のパーセント (%g) で、ggg.gg に丸められます）。

**グリッドなしで**

```
gmpe_as2008(
    eq::Earthquake,
    config::Params_as2008,
    VS30::Number=350,
    distance::Int64=1000
)
```

ここで `VS30=30` [m/s^2]、`distance=1000` [km] がデフォルトです。

出力は、`1:distance` の `pga` 値を持つ 1 次元 `Array{Float64}` になります（これは重力の加速度のパーセント (%g) で、ggg.gg に丸められます）。

**例:**

```
gmpe_as2008(eq,config_as2008,grid) # グリッド上でのPGA
gmpe_as2008(eq,config_as2008) # 入力グリッドなしで
```

**モデルパラメータ**

`examples/as-2008.conf` を参照してください。
