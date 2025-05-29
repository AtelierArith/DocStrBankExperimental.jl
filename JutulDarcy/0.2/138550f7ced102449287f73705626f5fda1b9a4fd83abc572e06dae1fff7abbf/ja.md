```
EquilibriumRegion(model, p_datum = missing,
    datum_depth = missing;
    woc = NaN,
    goc = NaN,
    wgc = NaN,
    pc_woc = 0.0,
    pc_goc = 0.0,
    pc_wgc = 0.0,
    temperature = missing,
    temperature_vs_depth = missing,
    composition = missing,
    composition_vs_depth = missing,
    liquid_composition = missing,
    liquid_composition_vs_depth = missing,
    vapor_composition = missing,
    vapor_composition_vs_depth = missing,
    density_function = missing,
    rs = 0.0,
    rs_vs_depth = missing,
    rv = 0.0,
    rv_vs_depth = missing,
    pvtnum = 1,
    satnum = 1,
    cells = missing,
    kwarg...
)
```

貯留層モデルのための平衡領域を設定します。この領域は、基準圧力と深さ、そして水-油、ガス-油、および水-ガス接触によって定義されます。接触は、領域内の相分布と初期圧力を決定するために使用されます。領域は、温度、組成、密度、およびrs/rv関数によってさらに指定できます。ほとんどのエントリは、深さの関数として指定するか、定数値として指定することができます。追加のキーワード引数は、`equilibriate_state`関数に渡されます。
