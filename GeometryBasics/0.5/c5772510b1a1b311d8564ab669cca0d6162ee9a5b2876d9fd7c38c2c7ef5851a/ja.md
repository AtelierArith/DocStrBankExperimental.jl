```
TupleView{T, N, Skip, A}
```

TupleViewは、配列の要素をタプルとしてグループ化します。Nはタプルの次元で、Mは次のタプルにスキップする要素の数を示します。デフォルトでは、TupleView{N}はN個のアイテムをスキップするように設定されています。

# いくつかの例:

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

TupleViewはreinterpretと一緒に使用できます:

```julia
x = [1, 2, 3, 4]
y = reinterpret(Point{2, Int}, TupleView{2, 1}(x))
> [Point(1, 2), Point(2, 3), Point(3, 4)]
```
