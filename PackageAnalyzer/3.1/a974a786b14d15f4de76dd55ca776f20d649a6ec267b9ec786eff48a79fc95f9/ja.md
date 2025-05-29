```
find_packages(; registries=reachable_registries())) -> Vector{PkgSource}
find_packages(names::AbstractString...; registries=reachable_registries()) -> Vector{PkgSource}
find_packages(names; registries=reachable_registries()) -> Vector{PkgSource}
```

指定されたレジストリ（`registry`キーワード引数で指定）内のすべてのパッケージを見つけます。デフォルトでは[General](https://github.com/JuliaRegistries/General)レジストリです。レジストリ内の各パッケージのディレクトリを指す[`PkgSource`](@ref)のベクターを返します。

パッケージの`names`のリストを最初の引数として渡すことで、それらのパッケージに対応するパスを返すか、個別のパッケージ名を別々の引数として渡します。
