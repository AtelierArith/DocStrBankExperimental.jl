```
Documenter{T}(;
    make_jl="~/.julia/packages/PkgTemplates/MepaC/templates/docs/make.jlt",
    index_md="~/.julia/packages/PkgTemplates/MepaC/templates/docs/src/index.md",
    assets=String[],
    logo=Logo(),
    canonical_url=make_canonical(T),
    devbranch=nothing,
    edit_link=:devbranch,
    makedocs_kwargs=Dict{Symbol,Any}(),
)
```

[Documenter.jl](https://github.com/JuliaDocs/Documenter.jl)を介してドキュメント生成を設定します。ドキュメントのデプロイは`T`に依存し、`T`はサポートされているCIプラグインのいずれか、またはローカルドキュメントビルドのみをサポートするための`Nothing`です。

!!! note
    GitHub ActionsまたはTravis CIでドキュメントをデプロイする場合は、[必要な設定](https://documenter.juliadocs.org/stable/man/hosting/#Hosting-Documentation)を完了することを忘れないでください。特に、次のコマンドを実行する必要があります。

    ```julia
    using DocumenterTools; DocumenterTools.genkeys(user="MyUser", repo="MyPackage.jl")
    ```

    そして、そこにある指示に従ってください。


## サポートされている型パラメータ

  * `GitHubActions`: [`GitHubActions`](@ref)の助けを借りて、ドキュメントを[GitHub Pages](https://pages.github.com)にデプロイします。
  * `TravisCI`: [`TravisCI`](@ref)の助けを借りて、ドキュメントを[GitHub Pages](https://pages.github.com)にデプロイします。
  * `GitLabCI`: [`GitLabCI`](@ref)の助けを借りて、ドキュメントを[GitLab Pages](https://pages.gitlab.com)にデプロイします。
  * `NoDeploy`（デフォルト）: ドキュメントのデプロイを設定しません。

## キーワード引数

  * `make_jl::AbstractString`: `make.jl`のテンプレートファイル。
  * `index_md::AbstractString`: `index.md`のテンプレートファイル。
  * `assets::Vector{<:AbstractString}`: 生成されたサイトのための追加アセット。
  * `logo::Logo`: ドキュメントロゴ情報を含む[`Logo`](@ref)。
  * `canonical_url::Union{Function, Nothing}`: サイトの正規URLを生成する関数。デフォルト値は、[`TravisCI`](@ref)および[`GitLabCI`](@ref)のためにそれぞれGitHub PagesおよびGitLab PagesのURLを計算します。`nothing`に設定すると、正規URLは設定されません。
  * `edit_link::Union{AbstractString, Symbol, Nothing}`: "Edit on…"リンクが指すブランチ、タグ、またはコミット。デフォルトは`devbranch`によって特定されるブランチです。`edit_link=:commit`の場合、リンクはドキュメントがビルドされるときの最新のコミットを指します。`edit_link=nothing`の場合、"Edit on…"リンクは完全に隠されます。
  * `devbranch::Union{AbstractString, Nothing}`: ドキュメントのデプロイをトリガーするブランチ。`nothing`の場合、`Template`に従ってデフォルトのブランチが使用されます。
  * `makedocs_kwargs::Dict{Symbol,Any}`: `makedocs`に挿入される追加のキーワード引数。
