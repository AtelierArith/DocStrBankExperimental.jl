```
@optic expr
@o expr
```

Construct an optic from an expression containing property/index access, function calls, and more.

Inside the macro, `_` is used as the placehold to refer to the target object.

The two forms, `@optic` and `@o`, are equivalent. We recommend using `@o` for brevity unless there is a potential for confusion.

# Example

```jldoctest
julia> using Accessors

julia> struct T;a;b;end

julia> t = T("A1", T(T("A3", "B3"), "B2"))
T("A1", T(T("A3", "B3"), "B2"))

julia> l = @optic _.b.a.b
(@o _.b.a.b)

julia> l(t)
"B3"

julia> set(t, l, 100)
T("A1", T(T("A3", 100), "B2"))

julia> t = ("one", "two")
("one", "two")

julia> set(t, (@o _[1]), "1")
("1", "two")

julia> l = @o _[∗].a
(@o _[∗].a)

julia> modify(x -> x + 1, ((a=1,), (a=2,)), l)
((a = 2,), (a = 3,))
```

See also [`@set`](@ref).
