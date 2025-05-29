```
get_var(
    xp::BifrostExperiment,
    snap::Union{<:Integer, AbstractVector{<:Integer}},
    variable::String,
    args...
    ;
    kwargs...
    )
```

`xp`の1つまたは複数のスナップショットから`variable`をロードします。

# 利用可能な変数

主な変数:

  * "r":  密度
  * "px": 運動量のx成分
  * "py": 運動量のy成分
  * "pz": 運動量のz成分
  * "e":  エネルギー

`if params["do_mhd"] == true`

  * "bx": 磁場のx成分
  * "by": 磁場のy成分
  * "bz": 磁場のz成分

補助変数（params["aux"]の変数）:

  * "p": 圧力
  * "tg": ガス温度   ...

# オプションのキーワード引数

変数を"si"または"cgs"単位に変換します: `units="si"`または`units="cgs"`。

変数のスライスをロードするには、例えば`slicex=[32, 410]`または`slicey=40:90`を指定します。

# 使用例:

```{julia}
exp_name = "cb24oi"
exp_dir = "/mn/stornext/d21/RoCS/matsc/3d/run/cb24oi"
snap = 700

xp = BifrostExperiment(expname, expdir)

# si単位で全立方体の圧力をロード
pressure = get_var(xp, snap, "p"; units="si")

# cgs単位でxy平面に沿ったスライスのガス密度をロード
rho = get_var(xp, snap, "r"; units="cgs", slicez=[100])
```
