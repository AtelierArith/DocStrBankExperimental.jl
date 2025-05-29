```
@gapattribute
```

このマクロは、引数の型が `T` である単項関数 `attr` のメソッド定義に適用されることを意図しています。コードには、`GAP.Globals.Something(X)` という形式の呼び出しが正確に1回含まれており、`Something` は `Centre` や `IsSolvableGroup` などのGAP属性であり、`attr` はその引数に対する対応する属性値を返します。

このマクロは、`attr`、`has_attr`、および `set_attr` の3つの関数を定義します。`attr` は型 `T` の引数を取り、与えられたメソッド定義が示すものを返します。`has_attr` は型 `T` の引数を取り、`GAP.Globals.HasSomething(X)` の結果（`true` または `false` のいずれか）を返します。`set_attr` は型 `T` の引数とオブジェクト `obj` を取り、`GAP.Globals.SetSomething(X, obj)` を呼び出します。

`GAP.Globals.Something` などを介したランタイムアクセスを避けるために、[`@gapwrap`](@ref) によって適用される3つの関数の構築に同じ修正が適用されます。

マクロによって作成される変数は、マクロが呼び出されるスコープにあるJuliaモジュールに属します。

# 例

```jldoctest
julia> @gapattribute isstrictlysortedlist(obj::GapObj) = GAP.Globals.IsSSortedList(obj)::Bool;

julia> l = GapObj([ 1, 3, 7 ]);

julia> has_isstrictlysortedlist( l )
false

julia> isstrictlysortedlist( l )
true

julia> has_isstrictlysortedlist( l )
true

julia> l = GapObj([ 1, 3, 7 ]);

julia> has_isstrictlysortedlist( l )
false

julia> set_isstrictlysortedlist( l, true )

julia> has_isstrictlysortedlist( l )
true

julia> isstrictlysortedlist( l )
true

```
