```
append!(xf::Transducer, dest, src) -> dest
```

このAPIは[`into` in Clojure](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/into)をモデルにしています。

!!! warning
    `append!(dest, src::Eduction)`のパフォーマンスは悪いです。二引数形式が好ましい場合は、代わりに`append!!`を使用してください。


# 例

```jldoctest
julia> using Transducers

julia> append!(Drop(2), [-1, -2], 1:5)
5-element Vector{Int64}:
 -1
 -2
  3
  4
  5
```
