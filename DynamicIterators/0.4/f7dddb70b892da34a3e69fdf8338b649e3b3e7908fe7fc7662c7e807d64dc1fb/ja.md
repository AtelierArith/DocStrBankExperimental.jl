```
進化
```

進化は次のように定義されます

```
    evolve(iter, value::T)::T
```

おそらく次のように

```
    evolve(iter, key=>value)
```

それらは `HasEltype()` と `eltype(iter) == T` を保証します。
