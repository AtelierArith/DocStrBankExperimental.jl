```
@docs パッケージ名
```

以前に `add_pkg_docs` を呼び出して記録されたパッケージのドキュメントサイトのURLを取得するか、そうでなければパッケージのリポジトリのURLを取得します。 そのURLをユーザーのデフォルトブラウザで開きます。

# 例

```
julia> using PkgOnlineHelp

julia> @docs StaticArrays
"https://github.com/JuliaArrays/StaticArrays.jl.git"
```

`StaticArrays` リポジトリサイトが返され、ブラウザで開かれます。この例では、ユーザーは以前に `add_pkg_docs` を呼び出して実際のドキュメントサイトに入っていませんでした。リポジトリサイトは `DEPOT_PATH` 内のすべてのJuliaレジストリを検索することで見つかりました。

`@docs` は、登録されていないパッケージや任意のウェブサイトにアクセスするためにも使用できます。たとえば、マクロについて説明しているJuliaのドキュメントの部分に迅速にアクセスしたい場合、次のようにJuliaプロンプトで一度だけ入力します。

```julia
julia> add_pkg_docs("macros", "https://docs.julialang.org/en/v1/manual/metaprogramming/#man-macros")
```

このJuliaセッションの後、または今後のセッションで、次のように入力することでサイトを迅速に開くことができます。

```julia
julia> @docs macros
```

もちろん、この例では `using PkgOnlineHelp` がすでに入力されていることを前提としています。便利のために、この文を `startup.jl` ファイルに含めることをお勧めします。

# 参照

`add_pkg_docs`, `remove_pkg_docs`, `list_pkg_docs`, `pkg_site`
