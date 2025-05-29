```
TravisCI(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/travis.yml",
    linux=true,
    osx=false,
    windows=false,
    x64=true,
    x86=false,
    arm64=false,
    coverage=true,
    extra_versions=["1.6", "1.11", "nightly"],
)
```

あなたのパッケージを[Travis CI](https://travis-ci.com)と統合します。

## キーワード引数

  * `file::AbstractString`: `.travis.yml`のテンプレートファイル。
  * `linux::Bool`: Linuxでビルドを実行するかどうか。
  * `osx::Bool`: OSX（MacOS）でビルドを実行するかどうか。
  * `windows::Bool`: Windowsでビルドを実行するかどうか。
  * `x64::Bool`: 64ビットアーキテクチャでビルドを実行するかどうか。
  * `x86::Bool`: 32ビットアーキテクチャでビルドを実行するかどうか。
  * `arm64::Bool`: ARM64アーキテクチャでビルドを実行するかどうか。
  * `coverage::Bool`: コードカバレッジを公開するかどうか。[`Codecov`](@ref)のような別のコードカバレッジプラグインも含める必要があります。
  * `extra_versions::Vector`: テストする追加のJuliaバージョン、文字列または`VersionNumber`として。
