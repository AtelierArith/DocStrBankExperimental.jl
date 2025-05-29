```
DroneCI(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/drone.star",
    amd64=true,
    arm=false,
    arm64=false,
    extra_versions=["1.6", "1.11"],
)
```

あなたのパッケージを[Drone CI](https://drone.io)と統合します。

## キーワード引数

  * `file::AbstractString`: `.drone.star`のテンプレートファイル。
  * `destination::AbstractString`: リポジトリのルートに対するファイルの宛先。たとえば、デフォルトのStarlarkファイルの代わりに`.drone.yml`を生成したいかもしれません。
  * `amd64::Bool`: AMD64でビルドを実行するかどうか。
  * `arm::Bool`: ARM（32ビット）でビルドを実行するかどうか。
  * `arm64::Bool`: ARM64でビルドを実行するかどうか。
  * `extra_versions::Vector`: テストする追加のJuliaバージョン、文字列または`VersionNumber`として。

!!! note
    ナイトリービルドのJuliaはサポートされていません。

