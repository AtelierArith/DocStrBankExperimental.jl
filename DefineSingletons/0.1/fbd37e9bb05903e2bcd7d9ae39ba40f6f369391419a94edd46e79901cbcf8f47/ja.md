```
@def_singleton singleton_name
@def_singleton singleton_name::SingletonType
@def_singleton singleton_name::SingletonType <: SuperType
@def_singleton singleton_name isa SuperType
@def_singleton singleton_name = SingletonType()
```

`s.singleton_name`という名前のシングルトンと、その2引数の`show(::IO, ::SingletonType)`メソッドを定義します。

`s.singleton_name = SingletonType()`の形式では、`SingletonType`は`Base.issingletontype(SingletonType)`が`true`である限り、パラメトリック型であることができます。

# 例

```jldoctest
julia> using DefineSingletons

julia> @def_singleton mysingleton::MySingletonType;

julia> mysingleton
mysingleton

julia> mysingleton isa MySingletonType
true

julia> mysingleton === MySingletonType()
true
```

スーパタイプを使った場合:

```jldoctest; setup = :(using DefineSingletons)
julia> abstract type MySuperType end;

julia> @def_singleton mysingleton2::MySingletonType2 <: MySuperType;

julia> mysingleton2
mysingleton2

julia> mysingleton2 isa MySingletonType2
true

julia> MySingletonType2 <: MySuperType
true

julia> @def_singleton mysingleton3 isa MySuperType;

julia> mysingleton3 isa MySuperType
true
```

既存のパラメトリック型を使った場合:

```jldoctest; setup = :(using DefineSingletons)
julia> struct MyParametricType{T} end;

julia> @def_singleton P1 = MyParametricType{1}();

julia> P1
P1

julia> P1 isa MyParametricType{1}
true
```
