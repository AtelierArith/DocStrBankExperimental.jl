```
RegistrySpec(name::String)
RegistrySpec(; name, url, path)
```

`RegistrySpec`は、[`PackageSpec`](@ref)のように、さまざまなメタデータを持つレジストリの表現です。

Pkgのほとんどのレジストリ関数は、`RegistrySpec`の`Vector`を受け取り、ベクター内のすべてのレジストリに対して操作を行います。

# 例

以下は、REPLモードと関数型APIの比較です::

| `REPL`               | `API`                                             |
|:-------------------- |:------------------------------------------------- |
| `MyRegistry`         | `RegistrySpec("MyRegistry")`                      |
| `MyRegistry=a67d...` | `RegistrySpec(name="MyRegistry", uuid="a67d...")` |
| `local/path`         | `RegistrySpec(path="local/path")`                 |
| `www.myregistry.com` | `RegistrySpec(url="www.myregistry.com")`          |
