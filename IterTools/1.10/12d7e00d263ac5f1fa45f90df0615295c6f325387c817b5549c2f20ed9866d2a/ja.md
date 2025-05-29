```
peekiter(xs)
```

イテレータの先頭要素を状態を更新せずに覗くことができます。

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
