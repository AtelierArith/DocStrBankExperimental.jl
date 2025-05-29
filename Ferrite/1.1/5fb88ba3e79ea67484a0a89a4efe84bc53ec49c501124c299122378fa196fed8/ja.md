```
PointIterator(ph::PointEvalHandler)
```

[`PointEvalHandler`](@ref)内のポイントに対するイテレータを作成します。イテレータの要素は、対応するポイントがグリッド内で見つかった場合は[`PointLocation`](@ref)であり、ポイントが見つからなかった場合は`nothing`です。

`PointLocation`は、`cellid`関数を使用してセルIDを照会するために使用でき、[`reinit!`](@ref)を使用して[`PointValues`](@ref)を再初期化するためにも使用できます。

# 例

```julia
ph = PointEvalHandler(grid, points)

for point in PointIterator(ph)
    point === nothing && continue # 見つからなかったポイントはスキップ
    reinit!(pointvalues, point)   # pointvaluesを更新
    # ...
end
```
