```
peekiter(xs)
```

Lets you peek at the head element of an iterator without updating the state.

```jldoctest
julia> it = peekiter(["face", "foo", "bar", "book", "baz", "zzz"]);

julia> peek(it)
Some("face")

julia> peek(it)
Some("face")

julia> x, s = iterate(it)
("face", ("foo", 3))

julia> x
"face"

julia> peek(it, s)
Some("foo")
```
