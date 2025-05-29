```
CirrusCI(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/cirrus.yml",
    image="freebsd-12-0-release-amd64",
    coverage=true,
    extra_versions=["1.6", "1.11", "nightly"],
)
```

あなたのパッケージを[Cirrus CI](https://cirrus-ci.org)と[CirrusCI.jl](https://github.com/ararslan/CirrusCI.jl)を介して統合します。

## キーワード引数

  * `file::AbstractString`: `.cirrus.yml`のテンプレートファイル。
  * `image::AbstractString`: 使用するFreeBSDイメージ。
  * `coverage::Bool`: コードカバレッジを公開するかどうか。[`Codecov`](@ref)も含める必要があります。
  * `extra_versions::Vector`: テストする追加のJuliaバージョン、文字列または`VersionNumber`として。

!!! note
    Cirrus CIからのコードカバレッジの提出は、まだ[Coverage.jl](https://github.com/JuliaCI/Coverage.jl)によってサポートされていません。

