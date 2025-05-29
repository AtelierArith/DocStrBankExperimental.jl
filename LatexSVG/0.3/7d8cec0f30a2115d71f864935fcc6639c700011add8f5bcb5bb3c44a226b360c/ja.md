```
LaTeXSVG(latex::AbstractString, svg::String; standalone::Bool=false)
```

この型は、レンダリングされるLaTeXコード、前文、およびレンダリングされたSVG文字列を含みます。両方の[`latexsvg`](@ref)および[`@Lsvg_str`](@ref)は、この型のオブジェクトを返します。

`LaTeXSVG`オブジェクトは4つのフィールドを含みます：

  * `latex`はLaTeX入力を含みます。
  * `standalone`は`latex`が完全なLaTeXドキュメントであるかどうかを示します。`standalone=true`の場合、`pre`は空です。
  * `pre`は、`LaTeXSVG`オブジェクトが構築されるとき、すなわち`latexsvg`または`@Lsvg_str`が呼び出されるときにグローバル前文から記録された文字列のベクターです。
  * `svg`はSVG文字列を含みます。

これらのフィールドには、通常のドット構文を使用してアクセスできます。

!!! note
    自分で`LaTeXSVG`オブジェクトを構築する必要はありません。


!!! note
    VSCodeを使用している場合、デフォルトでは、プロットペインに表示されるSVGの色はVSCodeのカラースキームに適応します（ライトモードでは黒、ダークモードでは白）。この適応色はSVG自体には書き込まれません。また、LaTeXでカスタムカラーを定義している場合、それは忠実に表示され（およびファイルに保存され）るはずです。

