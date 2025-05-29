```
req = @request expr
```

関数から求められる内部結果のリクエストを作成します。[`@espy`](@ref)の例として提示された関数を考慮すると、可能な構文の例には以下が含まれます。

```
req       = @request gp(s,z,material(a,b))
req       = @request gp(s)
req       = @request gp(material(a))
```

最初の式は次のように読むことができます。「関数内には変数`igp`に対する`do`ループがあり、そのループ内で`material`という関数が呼び出されています。ループ内からは結果`s`と`z`が求められ、`material`内からは結果`a`と`b`が求められます。」

各要素の結果を含む対応するデータ構造は`NTuples`と`NamedTuples`のネストであり、`out.gp[igp].material.a`などとしてアクセスできます。

参照: [`@espy`](@ref), [`@espydbg`](@ref)
