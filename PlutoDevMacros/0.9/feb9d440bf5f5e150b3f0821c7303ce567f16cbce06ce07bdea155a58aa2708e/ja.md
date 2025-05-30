```
only_in_nb(ex)
```

式 `ex` を、マクロが実行中の Pluto インスタンスから呼び出され、ソースノートブックファイルから直接実行された場合にのみ実行します。

これは `PlutoHooks.@skip_as_script` よりも厳格であり、別のノートブックから `@skip_as_script ex` を含むノートブックを読み込むと、`ex` は依然として実行されます。`@only_in_nb ex` は、呼び出し元のノートブックが元のソースノートブックファイルである場合にのみ `ex` を評価します。

関連情報: [`@only_out_nb`](@ref). [`PlutoHooks.@skip_as_script`](@ref).
