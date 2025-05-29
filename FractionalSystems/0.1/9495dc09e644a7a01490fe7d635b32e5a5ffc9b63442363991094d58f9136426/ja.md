```
fotfdata(G)
```

FOTFオブジェクトからデータを取得する

### 例

```julia-repl
julia> G = fotf([1, 2], [0.3, 0.4], [1, 2], [0.5, 0.6], 2)
julia> fotfdata(G)
5-element Vector{Any}:
  [1, 2]
  [0.5, 0.6]
  [1, 2]
  [0.3, 0.4]
 2
```
