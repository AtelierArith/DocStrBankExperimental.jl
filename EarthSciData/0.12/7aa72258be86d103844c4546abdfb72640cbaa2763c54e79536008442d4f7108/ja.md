```julia
partialderivatives_δPδlev_geosfp(geosfp; default_lev)

```

`δ(u)/δ(lev)`の偏微分演算子に掛ける係数を計算する関数を返します。これは、変数名`u`を`δ(u)/δ(lev)`から`δ(u)/δ(P)`に変換するためのもので、すなわち垂直レベル番号からhPaでの圧力への変換です。返される形式は`coordinate*index => conversion*factor`です。
