```
TupleView{T, N, Skip, A}
```

TupleView, groups elements of an array as tuples. N is the dimension of the tuple, M tells how many elements to skip to the next tuple. By default TupleView{N} defaults to skip N items.

# a few examples:

```julia

x = [1, 2, 3, 4, 5, 6]
TupleView{2, 1}(x):
> [(1, 2), (2, 3), (3, 4), (4, 5), (5, 6)]

TupleView{2}(x):
> [(1, 2), (3, 4), (5, 6)]

TupleView{2, 3}(x):
> [(1, 2), (4, 5)]

TupleView{3, 1}(x):
> [(1, 2, 3), (2, 3, 4), (3, 4, 5), (4, 5, 6)]
```

TupleView can be used together with reinterpret:

```julia
x = [1, 2, 3, 4]
y = reinterpret(Point{2, Int}, TupleView{2, 1}(x))
> [Point(1, 2), Point(2, 3), Point(3, 4)]
```
