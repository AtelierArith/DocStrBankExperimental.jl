```
function add_artifact!(
    artifacts_toml::String, name::String, tarball_url::String;
    clear=true,
    platform::Union{Platform,Nothing}=nothing,
    lazy::Bool=false,
    force::Bool=false
)
```

`tarball_url`からtarballをダウンロードし、それを抽出して`artifacts_toml`ファイルに名前`name`のアーティファクトとして追加します。`clear`がtrueの場合、アーティファクト自体はその後削除されます。残りのキーワード引数は`Pkg.Artifacts.bind_artifact!`に渡されます。

[そのドキュメント](https://julialang.github.io/Pkg.jl/dev/api/#Pkg.Artifacts.bind_artifact!)から:

> `platform`が`nothing`でない場合、このアーティファクトはプラットフォーム固有としてマークされ、マルチマッピングになります。同じ`artifacts_toml`内で異なる`platform`や`hash`を持つ同じ名前の複数のアーティファクトをバインドすることは有効です。`force`が`true`に設定されている場合、既存のマッピングが上書きされます。そうでない場合はエラーが発生します。
>
> [...] `lazy`が`true`に設定されている場合、ダウンロード情報が利用可能であっても、このアーティファクトは`artifact"name"`構文を介してアクセスされるか、`ensure_artifact_installed()`が呼び出されるまでダウンロードされません。

