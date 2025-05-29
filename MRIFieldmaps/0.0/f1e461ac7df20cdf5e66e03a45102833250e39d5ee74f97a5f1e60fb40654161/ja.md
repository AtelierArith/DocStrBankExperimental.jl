```
zdata, sos = coil_combine(ydata [, smap])
```

完全なマルチコイル画像データからB0フィールドマップを推定するには、まず複素コイル結合を行い、適切な重み付けのために合計二乗`sos`を追跡するだけで十分です。感度マップが提供されている場合、しばしば`sos`はすべて1と0になります。

感度マップが提供されていない場合、位相コントラストコイル結合アプローチ（以下の参考文献）を使用します。

# 入力

  * `ydata (dims..., nc, ne)` `ne ≥ 1` の複素画像セット、`nc ≥ 1` のコイル
  * `smap (dims..., nc)` 複素コイルマップ（オプション）

# 出力

  * `zdata (dims..., ne)` 複素コイル結合: `sum_c smap[c]' * ydata[c] ./ sos` または `sum_c ydata[c,1]' * ydata[c] ./ sos` （`smap`が提供されていない場合または`isnothing(smap)`の場合）
  * `sos (dims...)` 合計二乗: `sum_c |smap[c]|^2` または `sqrt.(sum_c |ydata[c,1]|^2` （`smap`が提供されていない場合または`isnothing(smap)`の場合）

M A Bernstein et al.の「Reconstructions of Phase Contrast, Phased Array Multicoil Data」、MRM 1994の式[13]を参照してください。 https://doi.org/10.1002/mrm.1910320308
