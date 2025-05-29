```
CachedTEX(doc::TEXDocument; kwargs...)
```

`TEXDocument`をコンパイルし、キャッシュされたTeXオブジェクトを返します。

`CachedTEX`構造体は、ドキュメントとそのコンパイルされた形式、およびプログラム内のバージョンへのポインタをいくつか保存します。また、ページの寸法も保存します。

`kwargs`には、内部関数`compile_latex`に渡すものを何でも指定できます。主に以下のものがあります：

  * `engine =`lualatex`/`xelatex`/...`: レンダリング時に使用するLaTeXエンジン
  * `options=`-file-line-error``:`latexmk`に渡すオプション。

コンストラクタは以下のフィールドを保存します：

  * `doc`
  * `pdf`
  * `ptr`
  * `surf`
  * `dims`

!!! note
    これは`mutable struct`です。なぜなら、Popplerハンドルへのポインタが変更される可能性があるからです。TODO: これをハンドルへのRefを持つ不変構造体にする?? あるいは、サーフェス自体を持つことも...


!!! note
    `doc`フィールドに`nothing`を指定して手動で`CachedTEX`を構築することも可能です。これは、事前にレンダリングされたPDFを図に挿入したい場合に便利です。

