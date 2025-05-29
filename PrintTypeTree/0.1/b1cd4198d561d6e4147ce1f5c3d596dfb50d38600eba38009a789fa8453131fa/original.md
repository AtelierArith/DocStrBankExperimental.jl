```
typetree(io=stdout, T)
```

Print type hierarchy tree.

For a type `T`, print

  * all the subtypes of `T`, recursively
  * the supertypes of `T` until `Any`
  * except the branch of `T`, the type tree of the children of the supertypes are   folded, but annotated with a visual cue of `(n children)` for those   having n > 0 children
  * the children of `Any` are hidden, and annotated with `(other children are hidden)`,   to avoid printing too many types
  * the type `T` is highlighted in red

# Examples

```julia julia> using PrintTypeTree julia> typetree(Integer) julia> # Note that the`Integer` will be highlighted in red Any (other children are hidden) └─ Number    ├─ Base.MultiplicativeInverses.MultiplicativeInverse (2 children)    ├─ Complex    └─ Real       ├─ AbstractFloat (5 children)       ├─ AbstractIrrational (1 children)       ├─ Integer       │  ├─ Bool       │  ├─ Signed       │  │  ├─ BigInt       │  │  ├─ Int128       │  │  ├─ Int16       │  │  ├─ Int32       │  │  ├─ Int64       │  │  └─ Int8       │  └─ Unsigned       │     ├─ UInt128       │     ├─ UInt16       │     ├─ UInt32       │     ├─ UInt64       │     └─ UInt8       └─ Rational
