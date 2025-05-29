**グリッド上**

  * Dlデータなしのグリッド上:

```
gmpe_mf2013(
    eq::Earthquake,
    config::Params_mf2013,
    grid::Array{Point_vs30};
    min_val::Number=0,
    Dl::Number=250,
    Xvf::Number=0
)
```

  * Dlデータありのグリッド上

```
gmpe_mf2013(
    eq::Earthquake,
    config::Params_mf2013,
    grid::Array{Point_vs30_dl};
    min_val::Number=0,
    Xvf::Number=0
)
```

ここで `min_val=0`、`Xvf=0` [km] がデフォルトです。`Dl=250` [km] は、`Dl`データなしでグリッドを通過する場合のデフォルトです。

出力は、`ground_motion > min_val` に基づく入力グリッドのポイントを持つ 1-d `Array{Point_<ground_motion_type>_out}` になります（`pga`,`psa` は重力の加速度のパーセント (%g) で、ggg.gg に丸められ、`pgv` は cm/s^2 です）。

**グリッドなし**

```
gmpe_as2008(
    eq::Earthquake,
    config::Params_mf2013;
    VS30::Number=350,
    distance::Int64=1000,
    Dl::Number=250,
    Xvf::Number=0
)
```

ここで `VS30=30` [m/s^2]、`distance=1000` [km]、`Xvf=0` [km]、`Dl=250` [km] がデフォルトです。

出力は、`pga`,`psa` の `1:distance` 値を持つ 1-d `Array{Float64}` になります（これは重力の加速度のパーセント (%g) で、ggg.gg に丸められたもの）または pgv [cm/s] です。

**例:**

```
gmpe_mf2013(
    eq,
    config_mf2013,
    grid
) # グリッド上のPGA,PGV,PSA用

gmpe_mf2013(
    eq,
    config_mf2013
) # 入力グリッドなしのPGA,PGV,PSA用
```

**モデルパラメータ**

`examples/morikawa-fujiwara-2013.conf` を参照してください。
