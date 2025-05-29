```
nth(xs, n)
```

`xs`の`n`番目の要素を返します。これは主にインデックス指定できないコレクションに便利です。

```jldoctest
julia> powers_of_two = iterated(x->2x,1);

julia> nth(powers_of_two, 4)
8
```
