```
@cbooify(Type_to_cbooify, (f1, f2, fa = Mod.f2...), callmethod=nothing, getproperty=getfield)
```

Allow functions of the form `f1(s::Type_to_cbooify, args...)` to also be called with `s.f1(args...)` with no performance penalty.

`callmethod` and `getproperty` are keyword arguments.

If an element of the `Tuple` is an assignment `sym = func`, then `sym` is the property that will call `func`. `sym` must be a simple identifier (a symbol). `func` is not required to be a symbol. For example `myf = Base._unexportedf`.

If `callmethod` is supplied, then `s.f1(args...)` is translated to `callmethod(s, f1, args...)` instead of `f1(s, args...)`.

`@cbooify` works by writing methods (or clobbering methods) for the functions `Base.getproperty` and `Base.propertnames`.

`getproperty` must be a function. If supplied, then it is called, rather than `getfield`, when looking up a property that is not on the list of functions. This can be useful if you want further specialzed behavior of `getproperty`.

`@cbooify` must by called after the definition of `Type_to_cbooify`, but may be called before the functions are defined.

If an entry is not function, then it is returned, rather than called.  For example `@cbooify MyStruct (y=3,)`. Callable objects meant to be called must be wrapped in a function.

# Examples:

  * Use within a module

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

  * The following two calls have the same effect.

```julia
@cbooify(Type_to_cbooify, (f1, f2, ...))

@cbooify(Type_to_cbooify, (f1, f2, ...) callmethod=nothing, getproperty=getfield)
```
