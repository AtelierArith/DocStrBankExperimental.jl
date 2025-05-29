```
maybe(optic; [default=nothing])
```

Create an optional optic that references a value that may or may not be present in the object.

**Note:** support for `default != nothing` is experimental and only implemented for getting, not for setting.

`maybe(o)` behaves similar to `o` itself, with the following differences:

  * if the referenced value is present, `set(obj, maybe(o), nothing)` deletes it
  * if the value is absent:

      * accessing `maybe(o)(obj)` returns `default`
      * `modify` doesn't do anything
      * `set` inserts the new value

Whether the referenced value is present or not, is determined by `hasoptic(obj, o)`.

`@maybe` is the macro form available for convenience: `@maybe ...` is equivalent to `maybe(@o ...)`.

## Examples

```julia
julia> o = maybe(@o _.a)

julia> o((a=1, b=2))
1
julia> o((b=2,))
# nothing

julia> set((a=1, b=2), o, 10)
(a = 10, b = 2)
julia> set((b=2,), o, 10)
(b = 2, a = 10)

julia> modify(x -> x+10, (a=1, b=2), o)
(a = 11, b = 2)
julia> modify(x -> x+10, (b=2,), o)
(b = 2,)

julia> modify(x -> x+10, ((a=1,), (a=2, b=3), (b=4,)), o ∘ Elements())
((a = 11,), (a = 12, b = 3), (b = 4,))
```
