`compute`(n, points, printformulaq = false)

Compute a formula for the nth order derivative using the given points.

```
            n: the n-th order derivative to be found
       points: in the format of a range, start : stop, or a vector
printformulaq: print the computed formula or not
```

|     points |                  The points/nodes to be used |
| ----------:| --------------------------------------------:|
|        0:2 |                         x[i], x[i+1], x[i+2] |
|       -2:2 |         x[i-2], x[i-1], x[i], x[i+1], x[i+2] |
|       -3:2 | x[i-3], x[i-2], x[i-1], x[i], x[i+1], x[i+2] |
| [1, 1, -1] |                               x[i-1], x[i+1] |
| [1 0 1 -1] |                         x[i-1], x[i], x[i+1] |

A vector can be like [1, 0, 2] or [1 0 2]. It will be rearranged so that elements are ordered from lowest to highest with duplicate ones removed.

# Examples

```julia-repl
julia> import FiniteDifferenceFormula as fd
julia> fd.compute(2, [0 1 2 3])
julia> fd.compute(2, 0:3)
julia> fd.compute(2, [-5, -2, 1, 2, 4], true)
```
