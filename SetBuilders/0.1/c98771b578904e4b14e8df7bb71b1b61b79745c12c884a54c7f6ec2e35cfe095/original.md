```
@setbuild([args...[; kwargs...]])
```

The `@setbuild` macro creates various SetBuilders sets.

The number of arguments varies depending on the type of set to create.

## No argument

  * EmptySet

```julia-repl
julia> @setbuild()
EmptySet()
```

## One argument

  * TypeSet

The first argument is any Julia type.

```julia-repl
julia> @setbuild(Integer)
TypeSet(Integer)
```

  * EnumerableSet

The first argument is a Vector with optionally Julia type

```julia-repl
julia> @setbuild([1, 2, 3])
EnumerableSet([{Int64}*3])

julia> @setbuild(Int32[])
EnumerableSet([{Int32}*0])
```

  * UniversalSet

The first argument is `Any` type

```julia-repl
julia> @setbuild(Any)
UniversalSet()
```

## Two arguments

  * PredicateSet

The first argument is the domain of the set. The second argument is the predicate of the set.

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> @setbuild(x in I, 0 <= x < 5)
PredicateSet((x ∈ TypeSet(Integer)) where 0 <= x < 5)
```

## Four arguments

  * MappedSet

The first argument is the domain of the set. The second argument is the codomain of the set. The third argument is the forward mapping of the set. The fourth argument is the backward mapping of the set.

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> @setbuild(x in I, y in I, y = x + 1, x = y - 1)
MappedSet((x ∈ TypeSet(Integer)) -> (y ∈ TypeSet(Integer)))
```

## Keyword arguments

The main usage of keyword arguments is to provide expressions inside of `@setbuild` with the objects defined outside of `@setbuild`.

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> k = 1
1

julia> @setbuild(x in I, y in I, y = x + c, x = y - c, c=k)
MappedSet((x ∈ TypeSet(Integer)) -> (y ∈ TypeSet(Integer)))
```

# Keywords

Keyword arguments are used to provide `@setbuild` macro with named references. For example, in previous code examples, `c=k` keyword argument provides `@setbuild` macro with the value of `k` so that `y = x + c` or `x = y - c` can be correctly evaluated.

!!! note
    keyword names starting with "sb_" are reserved for SetBuilders internal uses.

