```
@kwstruct Foo(b,a,c)
```

Equivalent to `@kwcall Foo(b,a,c)` plus a definition

```
Foo(nt::NamedTuple{(:b, :a, :c), T}) where {T} = Foo{(:b, :a, :c), T}(nt)
```

Note that this assumes existence of a `Foo` struct of the form

```
Foo{N,T} [<: SomeAbstractTypeIfYouLike]
    someFieldName :: NamedTuple{N,T}
end
```

NOTE: Default values (as in `@kwcall`) currently do not work for `@kwstruct`. They can work at the REPL, but this seems to be because of a world age issue. This feature may be supported again in a future release.
