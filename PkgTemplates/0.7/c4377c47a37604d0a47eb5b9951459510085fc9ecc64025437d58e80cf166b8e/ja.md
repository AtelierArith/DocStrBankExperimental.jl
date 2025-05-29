```
GitHubActions(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/github/workflows/CI.yml",
    destination="CI.yml",
    linux=true,
    osx=false,
    windows=false,
    x64=true,
    x86=false,
    coverage=true,
    extra_versions=["1.6", "1.11", "pre"],
)
```

あなたのパッケージを[GitHub Actions](https://github.com/features/actions)と統合します。

## キーワード引数

  * `file::AbstractString`: ワークフローファイルのテンプレートファイル。
  * `destination::AbstractString`: `.github/workflows`に対するワークフローファイルの宛先。
  * `linux::Bool`: Linuxでビルドを実行するかどうか。
  * `osx::Bool`: OSX（MacOS）でビルドを実行するかどうか。
  * `windows::Bool`: Windowsでビルドを実行するかどうか。
  * `x64::Bool`: 64ビットアーキテクチャでビルドを実行するかどうか。
  * `x86::Bool`: 32ビットアーキテクチャでビルドを実行するかどうか。
  * `coverage::Bool`: コードカバレッジを公開するかどうか。[`Codecov`](@ref)のような別のコードカバレッジプラグインも含める必要があります。
  * `extra_versions::Vector`: テストする追加のJuliaバージョン（文字列または`VersionNumber`）。

!!! note
    カバレッジプラグインを使用する場合は、[こちら](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets#creating-encrypted-secrets)に記載されているように、APIトークンを手動でシークレットとして追加するのを忘れないでください。

