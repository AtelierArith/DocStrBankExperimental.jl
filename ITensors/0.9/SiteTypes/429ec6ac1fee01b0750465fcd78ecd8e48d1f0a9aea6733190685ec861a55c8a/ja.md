```
val(s::Index, name::String)
```

特定の値の `name` に対応する整数を返します。つまり、`val` 関数は文字列を `1:dim(s)` の範囲内の特定の整数値にマッピングします。

`val` 関数は、Index `s` のタグの1つに対応する `SiteType` 引数を取り、入力名に対応する `ValName"name"` 引数を取る `val` という名前のメソッドをオーバーロードすることによって、さまざまな Index タグに対して実装されています。

# 例

```julia
s = Index(2, "Site,S=1/2")
val(s,"Up") == 1
val(s,"Dn") == 2

s = Index(2, "Site,Fermion")
val(s,"Emp") == 1
val(s,"Occ") == 2
```
