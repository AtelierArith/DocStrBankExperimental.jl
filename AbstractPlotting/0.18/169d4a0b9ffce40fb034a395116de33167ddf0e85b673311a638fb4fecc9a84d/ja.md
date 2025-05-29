```
density(values; npoints = 200, offset = 0.0, direction = :x)
```

`values`のカーネル密度推定をプロットします。`npoints`は推定の解像度を制御し、`offset`で基準線をシフトさせることができ、`direction`は:xまたは:yに設定できます。`bandwidth`と`boundary`はデフォルトで自動的に決定されます。

`color`は通常単一の色に設定されますが、グラデーションで色付けするために`:x`または`:y`に設定することもできます。`direction = :x`のときに`:y`を使用する場合（またはその逆）、2要素のカラーマップのみが正しく機能することに注意してください。

## 属性

`AbstractPlotting.Combined{AbstractPlotting.density!}`の利用可能な属性とそのデフォルトは次のとおりです: 

```

```
