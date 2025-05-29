```
url = pkg_docs_site(package::String; autoopen=true)
```

パッケージのドキュメントサイトのURLを、以前の`add_pkg_docs`呼び出しによって確立されたローカルデータベースを検索することで見つけようとします。要求されたパッケージのデータベースにエントリがない場合、パッケージリポジトリのURLは`pkg_site`を呼び出すことで取得されます。`autoopen`が`true`（デフォルト）である場合、URLはデフォルトのブラウザを使用して開かれます。

# 例

以前の（または現在の）Juliaセッションでユーザーが次のように入力したと仮定します。

```
julia> using PkgOnlineHelp

julia> add_pkg_docs("PSSFSS", "https://simonp0420.github.io/PSSFSS.jl/stable/")
```

その後、同じまたは後のJuliaセッションで：

```
julia> using PkgOnlineHelp

julia> pkg_docs_site("PSSFSS")
"https://simonp0420.github.io/PSSFSS.jl/stable/"
```

さらに、サイトはユーザーのデフォルトブラウザで開かれます。
