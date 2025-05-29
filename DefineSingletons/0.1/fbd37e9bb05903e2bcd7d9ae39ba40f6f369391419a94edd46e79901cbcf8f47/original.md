```
@def_singleton singleton_name
@def_singleton singleton_name::SingletonType
@def_singleton singleton_name::SingletonType <: SuperType
@def_singleton singleton_name isa SuperType
@def_singleton singleton_name = SingletonType()
```

Define a singleton named `singleton_name` and its two-argument `show(::IO, ::SingletonType)` method.

With the form `singleton_name = SingletonType()`, the type `SingletonType` can be a parametric type as long as `Base.issingletontype(SingletonType)` is `true`.

# Examples

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

With supertype:

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

With pre-existing parametric type:

```jldoctest; setup = :(using DefineSingletons)
julia> struct MyParametricType{T} end;

julia> @def_singleton P1 = MyParametricType{1}();

julia> P1
P1

julia> P1 isa MyParametricType{1}
true
```
