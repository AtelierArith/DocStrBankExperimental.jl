```
AppVeyor(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/appveyor.yml",
    x86=false,
    coverage=true,
    extra_versions=["1.6", "1.11", "nightly"],
)
```

あなたのパッケージを[AppVeyor](https://appveyor.com)を介して[AppVeyor.jl](https://github.com/JuliaCI/Appveyor.jl)と統合します。

## キーワード引数

  * `file::AbstractString`: `.appveyor.yml`のテンプレートファイル。
  * `x86::Bool`: 64ビットビルドに加えて、32ビットシステムでビルドを実行するかどうか。
  * `coverage::Bool`: コードカバレッジを公開するかどうか。[`Codecov`](@ref)も含める必要があります。
  * `extra_versions::Vector`: テストする追加のJuliaバージョン、文字列または`VersionNumber`として。
