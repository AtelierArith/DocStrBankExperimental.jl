```
@dotcallify(Type_to_dotcallify, (f1, f2, fa = Mod.f2...), callmethod=nothing, getproperty=getfield)
```

`f1(s::Type_to_dotcallify, args...)` の形の関数も `s.f1(args...)` で呼び出すことができ、パフォーマンスのペナルティはありません。

`callmethod` と `getproperty` はキーワード引数です。

`Tuple` の要素が `sym = func` の場合、`sym` は `func` を呼び出すプロパティです。`sym` は単純な識別子（シンボル）でなければなりません。`func` はシンボルである必要はありません。例えば `myf = Base._unexportedf` のように。

`callmethod` が指定されている場合、`s.f1(args...)` は `f1(s, args...)` の代わりに `callmethod(s, f1, args...)` に変換されます。

`@dotcallify` は `Base.getproperty` と `Base.propertnames` のためのメソッドを書いたり、上書きしたりすることで機能します。

`getproperty` は関数でなければなりません。指定されている場合、関数リストにないプロパティを検索する際に `getfield` の代わりに呼び出されます。これは、`getproperty` のさらなる特化した動作を望む場合に便利です。

`@dotcallify` は `Type_to_dotcallify` の定義の後に呼び出されなければなりませんが、関数が定義される前に呼び出すこともできます。

エントリが関数でない場合、それは呼び出されるのではなく返されます。例えば `@dotcallify MyStruct (y=3,)` のように。呼び出されることを意図したオブジェクトは関数でラップされる必要があります。

# 例:

  * モジュール内での使用

```julia
module Amod
import DotCall

struct A
    x::Int
end

DotCall.@dotcallify A (w, z)

w(a::A, y) = a.x + y
z(a::A, x, y) = a.x + y + x
end # module
```

```julia-repl
julia> a = Amod.A(3);

julia> Amod.w(a, 4) == a.w(4) == 7
true

julia> DotCall.whichmodule(a)
Main.Amod

julia> DotCall.dotcallified_properties(a)
(w = Main.Amod.w, z = Main.Amod.z)
```

  * 次の2つの呼び出しは同じ効果を持ちます。

```julia
@dotcallify(Type_to_dotcallify, (f1, f2, ...))

@dotcallify(Type_to_dotcallify, (f1, f2, ...) callmethod=nothing, getproperty=getfield)
```
