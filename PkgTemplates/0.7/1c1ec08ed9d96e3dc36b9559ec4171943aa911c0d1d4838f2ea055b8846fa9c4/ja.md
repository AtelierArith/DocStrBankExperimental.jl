```
GitLabCI(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/gitlab-ci.yml",
    coverage=true,
    extra_versions=["1.6", "1.11"],
)
```

あなたのパッケージを[GitLab CI](https://docs.gitlab.com/ce/ci)と統合します。

## キーワード引数

  * `file::AbstractString`: `.gitlab-ci.yml`のテンプレートファイル。
  * `coverage::Bool`: コードカバレッジを計算するかどうか。
  * `extra_versions::Vector`: テストする追加のJuliaバージョン（文字列または`VersionNumber`）。

## GitLab Pages

`Documenter{GitLabCI}`プラグインを含めることでドキュメントを生成できます。詳細については[`Documenter`](@ref)を参照してください。

!!! note
    ナイトリービルドのJuliaはサポートされていません。

