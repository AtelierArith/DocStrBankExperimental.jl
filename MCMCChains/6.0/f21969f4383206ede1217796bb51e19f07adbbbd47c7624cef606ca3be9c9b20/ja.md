```
forestplot(chains::Chains[, params::Vector{Symbol}]; kwargs...)
```

パラメータ `params` のサンプルに対してフォレストプロットまたはキャタピラープロットを生成します。

デフォルトでは、すべてのパラメータがプロットされます。

## キーワード引数

  * `ordered` (デフォルト: `false`): `ordered = false` の場合、フォレストプロットが生成されます。`ordered = true` の場合、キャタピラープロットが生成されます。
  * `fill_q` (デフォルト: `false`) および `fill_hpd` (デフォルト: `true`): 量子区間の曲線の下の領域を塗りつぶすか (`fill_q = true`)、または最高 posterior density (HPD) 区間を塗りつぶすか (`fill_hpd = true`)。`fill_q = false` および `fill_hpd = false` の場合、曲線の下の全領域が塗りつぶされます。塗りつぶし色が不要な場合は、シリーズ属性で指定する必要があります。これらのオプションは相互に排他的です。
  * `show_mean` (デフォルト: `true`) および `show_median` (デフォルト: `true`): posterior density estimate の平均 (`show_mean = true`) または中央値 (`show_median = true`) の垂直線をプロットします。両方のオプションが `true` に設定されている場合、両方の線がプロットされます。
  * `show_qi` (デフォルト: `false`) および `show_hpdi` (デフォルト: `true`): 各密度プロットの下部に量子区間 (`show_qi = true`) または最大 HPD 区間 (`show_hpdi = true`) をプロットします。これらのオプションは相互に排他的です。
  * `q` (デフォルト: `[0.1, 0.9]`): `fill_q = true` または `show_qi = true` の場合にプロットに使用される2つの量子。
  * `hpd_val` (デフォルト: `[0.05, 0.2]`): `fill_hpd = true` または `show_hpdi = true` の場合にプロットされる最高 posterior density 区間の補完確率質量。
