`compute`(n, points, printformulaq = false)

与えられた点を使用してn次導関数の式を計算します。

```
            n: 求めるn次導関数
       points: 範囲の形式で、start : stop、またはベクトル
printformulaq: 計算された式を表示するかどうか
```

|     points |                                    使用する点/ノード |
| ----------:| --------------------------------------------:|
|        0:2 |                         x[i], x[i+1], x[i+2] |
|       -2:2 |         x[i-2], x[i-1], x[i], x[i+1], x[i+2] |
|       -3:2 | x[i-3], x[i-2], x[i-1], x[i], x[i+1], x[i+2] |
| [1, 1, -1] |                               x[i-1], x[i+1] |
| [1 0 1 -1] |                         x[i-1], x[i], x[i+1] |

ベクトルは [1, 0, 2] または [1 0 2] のようになります。要素は最小から最大の順に並べ替えられ、重複は削除されます。

# 例

```julia-repl
julia> import FiniteDifferenceFormula as fd
julia> fd.compute(2, [0 1 2 3])
julia> fd.compute(2, 0:3)
julia> fd.compute(2, [-5, -2, 1, 2, 4], true)
```
