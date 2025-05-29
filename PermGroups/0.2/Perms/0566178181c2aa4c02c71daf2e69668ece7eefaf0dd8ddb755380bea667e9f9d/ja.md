`struct Perm{T<:Integer}`

Permは、集合`1:n`の順列を表し、1つのフィールドを持つ`struct`によって実装されています。フィールドは、`1:n`の画像を保持する`Vector{T}`です。REPLで`Perm`を表示すると、サイクル分解と、型が`Int16`でない場合はその型も表示されます。デフォルトのコンストラクタは、キーワード引数`check=false`が指定されない限り、入力をチェックします。

```julia-repl
julia> Perms.Perm_(UInt8[1,3,2,4])
Perm{UInt8}: (2,3)
```
