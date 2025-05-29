```
polimage(img::IntensityMap{<:StokesParams};
            colormap = :bone,
            colorrange = Makie.automatic,
            pcolorrange=Makie.automatic,
            pcolormap=Reverse(:jet1),
            nvec = 30,
            min_frac = 0.1,
            min_pol_frac=0.2,
            length_norm=1.0,
            plot_total=true)
```

画像 `img` を使用して偏光強度マップをプロットします。

プロットは [EHTC M87 Paper VII](https://iopscience.iop.org/article/10.3847/2041-8213/abe71d) の規則に従います。

ストークス `I` 画像は次の属性でプロットされます。

  * `colormap`
  * `colorrange`
  * `alpha`
  * `colorscale`

偏光画像はセットで構成されます。属性 `plot_total` は考慮される偏光量を変更します。

**`plot_total = true` の場合**

  * 総偏光が考慮され、マーカーは楕円で表示されます。
  * 楕円の向きは EVPA に等しいです。
  * 楕円の面積は `|V|²` に比例します。
  * 半長軸は総偏光強度に `length_norm` を掛けたものに関連しています。
  * 楕円の色は総偏光の分数にストークス `V` の符号を掛けたものによって決まります。

**`plot_total = false` の場合**

  * 線形偏光のみが考慮され、マーカーはティックで表示されます。
  * ティックの向きは EVPA に等しいです。
  * ティックの長さは総線形偏光強度、すなわち `√(Q² + U²)` に `length_norm` を掛けたものに等しいです。
  * ティックの色は線形偏光の分数によって決まります。

## 属性

  * `colormap`: ストークス `I` 画像のカラーマップ。デフォルトは `:bone` です。
  * `colorrange`: ストークス `I` 画像のカラーレンジ。デフォルトは `(0, maximum(stokes(img, :I)))` です。
  * `pcolorrange:` 偏光画像のカラーレンジ
  * `pcolormap`: 総/線形偏光マーカーに使用されるカラーマップ。
  * `nvec`: プロットする偏光ベクトルの数
  * `min_frac`: `I < min_frac*maximum(I)` のマーカーはプロットされません。
  * `min_pol_frac`: `P < min_frac*maximum(P)` のマーカーはプロットされません。ここで `P` は総/線形偏光フラックスです。
  * `length_norm`: ティックに使用される正規化を指定します。デフォルトは、最大偏光強度を持つピクセルのティック長がピクセル間隔の10倍になることです。最大偏光強度が 10Jy/μas² でピクセル間隔が 1μas の画像では、マーカーの長さは 10μas になります。
  * `plot_total`: true の場合は総偏光をプロットします。false の場合は線形偏光のみをプロットします。

!!! warning
    偏光プロットは天文学者/EHT 偏光規則を使用して本質的に定義されています。これは、偏光ティックを意味のある方法でプロットするためには、軸を定義する際に `xreversed=true` にする必要があることを意味します。

