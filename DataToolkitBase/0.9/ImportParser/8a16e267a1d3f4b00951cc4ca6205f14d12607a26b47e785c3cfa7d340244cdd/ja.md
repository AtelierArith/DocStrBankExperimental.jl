```
@import pkg1, pkg2...
@import pkg1 as name1, pkg2 as name2...
@import pkg: foo, bar...
@import pkg: foo as bar, bar as baz...
```

以前に `@addpkg` で登録されたモジュールを取得し、現在の名前空間にインポートします。このマクロは、`using` の構文を大まかに模倣しようとします。

型推論のために、小文字で始まるすべてのバインディングは関数であり、大文字で始まるバインディングは型であると仮定されます。例外は手動で型アサーションを使って注釈を付ける必要があります。

`@import` ステートメントのために必要なパッケージをロードする必要があった場合、`PkgRequiredRerunNeeded` シングルトンが返されます。

# 例

```julia
@import pkg
pkg.dothing(...)
# 代替形式
@import pkg: dothing
dothing(...)
```
