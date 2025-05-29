```
iterated(f, x)
```

`f`の連続適用を繰り返します。すなわち、`x`、`f(x)`、`f(f(x))`、`f(f(f(x)))`、...

必要な数の要素を取得するために`Base.Iterators.take()`を使用します。

```jldoctest
julia> for i in Iterators.take(iterated(x -> 2x, 1), 5)
           @show i
       end
i = 1
i = 2
i = 4
i = 8
i = 16

julia> for i in Iterators.take(iterated(sqrt, 100), 6)
           @show i
       end
i = 100
i = 10.0
i = 3.1622776601683795
i = 1.7782794100389228
i = 1.333521432163324
i = 1.1547819846894583
```
