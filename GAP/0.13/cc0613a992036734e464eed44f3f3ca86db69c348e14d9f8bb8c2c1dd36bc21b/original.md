```
@gapattribute
```

This macro is intended to be applied to a method definition for a unary function called `attr`, say, where the argument has the type `T`, say, the code contains exactly one call of the form `GAP.Globals.Something(X)`, where `Something` is a GAP attribute such as `Centre` or `IsSolvableGroup`, and `attr` returns the corresponding attribute value for its argument.

The macro defines three functions `attr`, `has_attr`, and `set_attr`, where `attr` takes an argument of type `T` and returns what the given method definition says, `has_attr` takes an argument of type `T` and returns the result of `GAP.Globals.HasSomething(X)` (which is either `true` or `false`), `set_attr` takes an argument of type `T` and an object `obj` and calls `GAP.Globals.SetSomething(X, obj)`.

In order to avoid runtime access via `GAP.Globals.Something` etc., the same modifications are applied in the construction of the three functions that are applied by [`@gapwrap`](@ref).

The variables that are created by the macro belong to the Julia module in whose scope the macro is called.

# Examples

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
