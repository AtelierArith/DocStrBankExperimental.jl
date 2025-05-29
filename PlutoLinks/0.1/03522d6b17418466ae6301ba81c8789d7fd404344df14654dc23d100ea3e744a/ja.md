`@revise` マクロは、Revise によって監視されているパッケージをインポートします。`@revise` が呼び出されるセルは、パッケージの定義が変更されるたびに再実行されます。これは、このパッケージに依存するセルも更新されることを意味します。

  * 修正されたパッケージは現在の環境で開発されるべきであり、通常は [Pluto パッケージマネージャからオプトアウトする必要があります](https://github.com/fonsp/Pluto.jl/wiki/%F0%9F%8E%81-Package-management#advanced-set-up-an-environment-with-pkgactivate)。

---

例

```julia
# 1つのセルで
using PlutoLinks

# 別のセルで
@revise using MyPackage

# インポートもサポートされています
@revise import MyPackage
```
