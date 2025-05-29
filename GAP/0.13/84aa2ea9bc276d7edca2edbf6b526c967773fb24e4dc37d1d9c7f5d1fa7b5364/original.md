```
@gapwrap
```

When applied to a method definition that involves access to entries of `GAP.Globals`, this macro rewrites the code such that the relevant GAP globals are cached, and need not be fetched again and again.

# Examples

```jldoctest
julia> @gapwrap isevenint(x) = GAP.Globals.IsEvenInt(x)::Bool;

julia> isevenint(1)
false

julia> isevenint(2)
true

```
