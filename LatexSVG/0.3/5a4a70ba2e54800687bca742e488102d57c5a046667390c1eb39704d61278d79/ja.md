```
config!(; texengine=nothing, preamble=nothing, export_prefs=false)
```

LaTeXエンジンと前文の永続的な設定を構成します：

  * `texengine` は [`XeLaTeX`](@ref)、[`PDFLaTeX`](@ref)、または [`LuaLaTeX`](@ref) で指定できます。
  * `preamble` は `AbstractString` または `AbstractString` の `Vector` で指定できます。

二つの例：

```julia-repl
julia> config!(texengine=PDFLaTeX)
```

これにより、デフォルトのLaTeXエンジンが `PDFLaTeX` に設定されます *すべての今後のセッションに対して*。

```julia-repl
julia> config!(preamble=["\usepackage{mathtools}", "\usepackage{xcolor}"])
```

これにより、デフォルトの前文が次のように設定されます。

```latex
\usepackage{mathtools}
\usepackage{xcolor}
```

*すべての今後のセッションに対して*、元のデフォルトの

```latex
\usepackage{amsmath,amsthm,amssymb}
\usepackage{color}
```

を置き換えます。

キーワード引数なしで `config!()` を呼び出すこともできます。この場合、現在のLaTeXエンジンと前文がデフォルトとして保存されます。

これらの設定は、アクティブなプロジェクト内の `LocalPreferences.toml` ファイルに保存されます。 `export_prefs=true` の場合、これらは `Project.toml` に書き込まれます。いずれにせよ、このパッケージを使用する複数のプロジェクトがある場合は、それぞれのプロジェクトに対して個別に設定を行う必要があります。
