`@ref` リンクが `@extref` リンクにフォールバックするためのプラグイン。

!!! warning
    このプラグインは `Documenter >= v1.3.0` でのみ利用可能であり、実験的なものと見なされるべきです。


```julia
fallbacks = ExternalFallbacks(pairs...)
```

は `@ref` スラグを `@external` リンクにマッピングします。もし `@ref` がローカルで解決できない場合、[`InterLinks`](@ref) プラグインがマッピングで定義された `@extref` リンクターゲットを使ってそれを解決します。

`@ref` スラグは、`Documenter` が `@ref` リンクを解決できないときに印刷するメッセージに見つけることができます。例えば、

```
Error: Cannot resolve @ref for 'makedocs' …
Error: Cannot resolve @ref for 'Other-Output-Formats'
```

は、解決できないリンク ```[`makedocs`](@ref)``` と `[Other Output Formats](@ref)` からのものです。

「スラグ」とは、引用符の中の文字列です。これは完全な `@extref` リンクにマッピングされるべきです。例えば、

```julia
fallbacks = ExternalFallbacks(
    "makedocs" => "@extref Documenter.makedocs",
    "Other-Output-Formats" =>  "@extref Documenter `Other-Output-Formats`",
)
```

これにより、リンク ```[`makedocs`](@ref)``` は、まるで ```[`makedocs`](@extref Documenter.makedocs)``` と書かれていたかのように解決され、`[Other Output Format](@ref)` は、まるで ```[Other Output Format](@extref Documenter `Other-Output-Formats`)``` と書かれていたかのように解決され、それぞれ [`makedocs`](@ref) と [Other Output Formats](@ref) にリンクします。
