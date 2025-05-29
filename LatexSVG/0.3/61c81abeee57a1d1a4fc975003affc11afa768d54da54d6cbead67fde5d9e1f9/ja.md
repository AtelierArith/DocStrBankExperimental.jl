```
latexsvg(latex::AbstractString, engine=texengine(); standalone=false, extra_args=[])
```

`latex`をSVG文字列としてレンダリングします。`latex`はレンダリングしたいLaTeXコードで、`engine`は使用するLaTeXエンジンで、デフォルトではこのセッションで現在使用されているものになります。このセッションのエンジンを変更するには[`texengine!`](@ref)を使用するか、デフォルトを永続的に設定するには[`config!`](@ref)を使用します。

出力は、いくつかのキーワード引数で構成できます：

  * `standalone=true`の場合、`latex`は完全なドキュメントであると見なされ、したがって前文は無視されます。それ以外の場合（これがデフォルトです）、`latex`はLaTeXドキュメントに挿入され、その前文は[`add_preamble!`](@ref)で構成でき、[`reset_preamble!`](@ref)でリセットできます。現在の完全な前文は[`preamble`](@ref)で取得できます。
  * `extra_args`を使用すると、LaTeXエンジンに追加のコマンドラインフラグ/引数を渡すことができます。たとえば、LaTeXコードに`minted`コードブロックが含まれている場合（何らかの理由で）、`extra_args=["--shell-escape"]`を設定する必要があります。
