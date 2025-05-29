```
@cbooify(Type_to_cbooify, (f1, f2, fa = Mod.f2...), callmethod=nothing, getproperty=getfield)
```

`f1(s::Type_to_cbooify, args...)` の形の関数も、パフォーマンスペナルティなしで `s.f1(args...)` として呼び出すことができるようにします。

`callmethod` と `getproperty` はキーワード引数です。

`Tuple` の要素が `sym = func` の形式である場合、`sym` は `func` を呼び出すプロパティです。`sym` は単純な識別子（シンボル）でなければなりません。`func` はシンボルである必要はありません。例えば `myf = Base._unexportedf` のように。

`callmethod` が指定されている場合、`s.f1(args...)` は `f1(s, args...)` の代わりに `callmethod(s, f1, args...)` に変換されます。

`@cbooify` は、関数 `Base.getproperty` と `Base.propertnames` のメソッドを作成（または上書き）することによって機能します。

`getproperty` は関数でなければなりません。指定された場合、関数リストにないプロパティを検索する際に `getfield` の代わりに呼び出されます。これは、`getproperty` のさらなる特化した動作を望む場合に便利です。

`@cbooify` は `Type_to_cbooify` の定義の後に呼び出されなければなりませんが、関数が定義される前に呼び出すこともできます。

エントリが関数でない場合、それは呼び出されるのではなく返されます。例えば `@cbooify MyStruct (y=3,)` のように。呼び出されることを意図したオブジェクトは、関数でラップする必要があります。

# 例:

  * モジュール内での使用

```julia
module Amod
import CBOOCall

struct A
    x::Int
end

CBOOCall.@cbooify A (w, z)

w(a::A, y) = a.x + y
z(a::A, x, y) = a.x + y + x
end # module
```

```julia-repl
julia> a = Amod.A(3);

julia> Amod.w(a, 4) == a.w(4) == 7
true

julia> CBOOCall.whichmodule(a)
Main.Amod

julia> CBOOCall.cboofied_properties(a)
(w = Main.Amod.w, z = Main.Amod.z)
```

  * 次の2つの呼び出しは同じ効果を持ちます。

```julia
@cbooify(Type_to_cbooify, (f1, f2, ...))

@cbooify(Type_to_cbooify, (f1, f2, ...) callmethod=nothing, getproperty=getfield)
```
