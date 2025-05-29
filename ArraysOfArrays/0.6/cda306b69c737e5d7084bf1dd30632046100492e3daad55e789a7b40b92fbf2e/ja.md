```
consgroupedview(source::AbstractVector, target)
```

`source`の等しい連続要素のグループ化を[`consgrouped_ptrs`](@ref)を介して計算し、そのグループ化を`target`、すなわち`target`の各要素に適用します。`target`はベクトルまたは名前付きまたは名前なしのベクトルのタプルである可能性があります。結果は`VectorOfVectors`、すなわちそのようなタプルになります。

例:

```
A = [1, 1, 2, 3, 3, 2, 2, 2]
B = [1, 2, 3, 4, 5, 6, 7, 8]
consgroupedview(A, B) == [[1, 2], [3], [4, 5], [6, 7, 8]]
```

`consgroupedview`は列指向のテーブルとも相性が良いです:

```julia
    using Tables, TypedTables
    data = Table(
        a = [1, 1, 2, 3, 3, 2, 2, 2],
        b = [1, 2, 3, 4, 5, 6, 7, 8],
        c = [1.1, 2.2, 3.3, 4.4, 5.5, 6.6, 7.7, 8.8]
    )

    result = Table(consgroupedview(data.a, Tables.columns(data)))
```

は次のように返します

```
     a          b          c
   ┌──────────────────────────────────────
 1 │ [1, 1]     [1, 2]     [1.1, 2.2]
 2 │ [2]        [3]        [3.3]
 3 │ [3, 3]     [4, 5]     [4.4, 5.5]
 4 │ [2, 2, 2]  [6, 7, 8]  [6.6, 7.7, 8.8]
```

データをコピーせずに:

```
    flatview(result.a) === data.a
    flatview(result.b) === data.b
    flatview(result.c) === data.c
```
