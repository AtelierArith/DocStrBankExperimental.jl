ソースコードを特定のレクサー、MIMEタイプ、およびテーマを使用してハイライトします。

```julia
highlight(io, mime, src, lexer)
highlight(io, mime, src, lexer, theme)

```

`src`は提供された`lexer`を使用してトークン化され、その後`theme`を使用して色付けされ、最終的に指定された形式`mime`で`io`に出力されます。`theme`はデフォルトで`Themes.DefaultTheme`テーマになります。

`mime`は`MIME("text/html")`または`MIME("text/latex")`のいずれかです。

# 例

```jldoctest
julia> using Highlights

julia> highlight(stdout, MIME("text/html"), "2x", Lexers.JuliaLexer)
<pre class='hljl'>
<span class='hljl-ni'>2</span><span class='hljl-n'>x</span>
</pre>

julia> highlight(stdout, MIME("text/latex"), "'x'", Lexers.JuliaLexer, Themes.VimTheme)
\begin{lstlisting}
(*@\HLJLsc{{\textquotesingle}x{\textquotesingle}}@*)
\end{lstlisting}

```
