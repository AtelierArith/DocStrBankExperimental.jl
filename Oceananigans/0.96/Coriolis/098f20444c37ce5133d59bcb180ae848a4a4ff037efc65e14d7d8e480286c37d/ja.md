```
ConstantCartesianCoriolis([FT=Float64;] fx=nothing, fy=nothing, fz=nothing,
                                        f=nothing, rotation_axis=ZDirection(),
                                        rotation_rate=Ω_Earth, latitude=nothing)
```

定常回転を `x`、`y`、`z` 方向に分解したパラメータオブジェクトを返します。海洋学において、成分 `x`、`y`、`z` はそれぞれ東、北、上の方向に対応します。この定常回転は、次の3つの異なる方法で指定できます：

  * すべての成分 `fx`、`fy`、`fz` を直接指定する。
  * コリオリパラメータ `f` を指定し、（オプションで）`rotation_axis` を指定する（指定しない場合は `z` 方向がデフォルトとなります）。
  * `latitude`（度単位）を指定し、（オプションで）ラジアン毎秒の `rotation_rate` を指定する（指定しない場合は地球の回転率がデフォルトとなります）。
