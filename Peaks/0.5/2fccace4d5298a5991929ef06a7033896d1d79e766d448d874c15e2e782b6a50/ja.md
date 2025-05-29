```
filterpeaks!(pred, pks) -> NamedTuple
```

名前付きタプルのスライス（各ピークに関連するスカラー値、例えば `(indices=5, heights=3, proms=2)`）に対して述語関数 `pred` を適用し、`pred` が `false` を返す場合はピークを削除します。

# 例

```jldoctest
julia> pks = findmaxima([0,5,2,3,3,1,4,0])
(indices = [2, 4, 7], heights = [5, 3, 4], data = [0, 5, 2, 3, 3, 1, 4, 0])

julia> filterpeaks!(pks) do nt
           return nt.heights ≥ 5 || nt.heights ≤ 3
       end
(indices = [2, 4], heights = [5, 3], data = [0, 5, 2, 3, 3, 1, 4, 0])
```
