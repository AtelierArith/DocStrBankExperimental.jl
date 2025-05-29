```
RecursiveOfType(out::Type, [optic=Children()]; [recurse::Type=Any])
```

任意の深さにある型 `out` のすべての値を参照するオプティック。

指定された内部の `optic` を使用して、型 `recurse`（デフォルトは `Any`）の値に再帰します。デフォルトの `Children()` は、オブジェクトのすべてのプロパティ、またはコレクションのすべての要素に降りていきます。

___注意:___ 通常、`optic` パラメータを変更する際には、`recurse` 型も絞り込むべきです。

## 例

```julia
julia> obj = ([1,2,3], (a=[4,5], b=[6], c=([7], [8,9])));

# オブジェクトからすべての数値を抽出する:
julia> getall(obj, RecursiveOfType(Number))
9-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
 7
 8
 9

# 各ベクターの最初の要素を抽出する:
julia> getall(obj, @o _ |> RecursiveOfType(Vector) |> first)
(1, 4, 6, 7, 8)

# 各ベクターの最初の要素を否定する:
julia> modify(x -> -x, obj, @o _ |> RecursiveOfType(Vector) |> first)
([-1, 2, 3], (a = [-4, 5], b = [-6], c = ([-7], [-8, 9])))
```
