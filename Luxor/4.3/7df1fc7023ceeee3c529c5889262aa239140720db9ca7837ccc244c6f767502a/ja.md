```
textlines(s::T where T <: AbstractString, width::Real;
     rightgutter=5)
```

`s`のテキストを幅`width`単位（現在のフォントで）までの行に分割します。

文字列の配列を返します。文字列の配列を描画するには`textwrap`を使用してください。

TODO: `rightgutter`オプションのキーワードは、列の右側にいくらかのパディングを追加します。これは時々必要なようです - おそらくアルゴリズムは`textextents`とスペースの相互作用を考慮するように改善する必要がありますか？
