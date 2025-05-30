```
colormap(cname, N=100; logscale=false, <keyword arguments>)
```

Wijffelaars, M. らによって計算された、事前定義された順次または発散カラーマップを返します (2008)。

順次カラーマップ `cname` の選択肢は次のとおりです：

  * `"Blues"`
  * `"Grays"`
  * `"Greens"`
  * `"Oranges"`
  * `"Purples"`
  * `"Reds"`

発散カラーマップの選択肢は `"RdBu"` です。

オプションで、色の数 `N` を指定できます（デフォルトは 100）。

キーワード引数によって追加の制御が提供されます。

  * `mid` は発散カラーマップの中点の位置を設定します。
  * `logscale=true` はカラーマップ内で対数間隔のステップを使用します。

また、[`sequential_palette`](@ref) または [`diverging_palette`](@ref) の引数名と一致するキーワード引数名を使用することもできます。
