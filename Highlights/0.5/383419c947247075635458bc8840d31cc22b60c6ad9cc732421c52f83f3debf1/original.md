Highlight source code using a specific lexer, mimetype and theme.

```julia
highlight(io, mime, src, lexer)
highlight(io, mime, src, lexer, theme)

```

`src` is tokenised using the provided `lexer`, then colourised using `theme`, and finally output to `io` in the given format `mime`. `theme` defaults to `Themes.DefaultTheme` theme.

`mime` can be either `MIME("text/html")` or `MIME("text/latex")`.

# Examples

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
