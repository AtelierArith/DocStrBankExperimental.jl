```
read_packages(registry::AbstractString; kwargs...)
read_packages(f, registry; recursive=true, kwargs...)
```

レジストリ `registry` に保存されているすべてのパッケージを読み込みます。

述語関数 `f` が指定されている場合、`f(pkg)==true` を満たすパッケージが返されるリストに追加されます。`recursive==true` の場合、すべての依存パッケージも返されるリストに追加されます。

キーワード引数:

  * `latest_versions_num::Integer`: 各パッケージの最新の `latest_versions_num` バージョンのみを取得します。
  * `fetch_full_registry::Bool = false`: `true` にすると、インクリメンタルパースを無効にします。

# 例

すべてのパッケージをリスト表示:

```julia
pkgs = read_packages("General")
```

JuliaArrays の下にあるパッケージのみをリスト表示:

```julia
pkgs = read_packages("General") do pkg
    occursin("JuliaArrays", pkg.url)
end
```
