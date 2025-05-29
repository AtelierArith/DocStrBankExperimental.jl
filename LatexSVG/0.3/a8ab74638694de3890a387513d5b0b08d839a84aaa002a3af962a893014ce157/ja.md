```
savesvg(filepath::AbstractString, svg::LaTeXSVG; web_display=false, web_inline=false)
```

`savesvg`を`filepath`に保存します。

`web_display=true`の場合、SVGが保存される前にいくつかの調整が行われます：

  * SVGの高さは1.2倍にスケーリングされ、その単位は`rem`に変更され、幅属性は削除されます。
  * スタイル属性`style="display: block; margin: auto; max-width: 80%"`が追加されます。
  * `<svg>`タグに`class="latexsvg-display"`属性が追加されます。

`web_inline=true`の場合、次の調整が行われます：

  * SVGの高さは1.2倍にスケーリングされ、その単位は`rem`に変更され、幅属性は削除されます。
  * スタイル属性`style="vertical-align: middle"`が追加されます。
  * `class="latexsvg-inline"`属性が追加されます。

詳細については、ドキュメントを参照してください。

`web_display`と`web_inline`は両方とも`true`にすることはできません。両方が`false`の場合、バニラSVG出力が変更なしで保存されます。
