```
RegularGrid(dims, origin, spacing)
```

次のように、`dims`の次元を持ち、左下隅が`origin`にあり、セルの間隔が`spacing`である正規グリッド。3つの引数は同じ長さでなければなりません。

```
RegularGrid(dims, origin, spacing, offset)
```

次のように、`dims`の次元を持ち、要素`offset`の左下隅が`origin`にあり、セルの間隔が`spacing`である正規グリッド。

```
RegularGrid(start, finish, dims=dims)
```

また、`start`ポイントから`finish`までの正規グリッドを`dims`の次元で構築します。

```
RegularGrid(start, finish, spacing)
```

また、与えられた`spacing`を使用して、`start`ポイントから`finish`ポイントまでの正規グリッドを構築します。

```
RegularGrid(dims)
RegularGrid(dim1, dim2, ...)
```

最後に、次元`dims`をタプルとして渡すか、各次元`dim1`、`dim2`、...を個別に渡すことで正規グリッドを構築できます。この場合、原点と間隔はそれぞれ(0,0,...)と(1,1,...)にデフォルト設定されます。

## 例

100x100x50の六面体を持つ3Dグリッドを作成します：

```julia
julia> RegularGrid(100, 100, 50)
```

100 x 100の四角形を持ち、原点が(10.0, 20.0)にある2Dグリッドを作成します：

```julia
julia> RegularGrid((100, 100), (10.0, 20.0), (1.0, 1.0))
```

-1から1までの100セグメントを持つ1Dグリッドを作成します：

```julia
julia> RegularGrid((-1.0,), (1.0,), dims=(100,))
```

[`CartesianGrid`](@ref)も参照してください。
