```julia
clone_registries_for_package(
    pkg::PackageSpec;
    registries_dir::AbstractString=get_registries_dir(),
    registries::Vector{Pkg.Registry.RegistryInstance} = Pkg.Registry.reachable_registries(),
)::Vector{Pkg.Registry.RegistryInstance}
```

指定されたパッケージのバージョンについて、対応するレジストリでのリリース日を確認します。次に、その指定された日付のすべてのレジストリをクローンします。

これにより、パッケージのリリース日まで時間を遡ったかのようにパッケージをインストールできます。

注意: 各レジストリは2回クローンされ、ダウンロードサイズを削減しようとします。

  * 一度目は、レジストリのGIT履歴のみを取得し、正しいコミットを見つけるためです。
  * 二度目は、そのコミットでのみレジストリをクローンするためです。

執筆時点では、一般レジストリのダウンロードサイズは約220 MBです。

# 例

```julia
using Pkg, RegistryTimeTraveler

# レジストリがインストールされるフォルダに移動
cd(pwd())

# パッケージとバージョンを選択
pkg = PackageSpec(name="JSON3", version="1.9.3")

cloned_registries = clone_registries_for_package(pkg)

# 非常に重要: Pkgがクローンされたレジストリを更新しないようにする!
Pkg.OFFLINE_MODE[] = true

Pkg.activate(".")
Pkg.add(pkg.name; registries=cloned_registries, preserve=Pkg.PRESERVE_NONE)

```
