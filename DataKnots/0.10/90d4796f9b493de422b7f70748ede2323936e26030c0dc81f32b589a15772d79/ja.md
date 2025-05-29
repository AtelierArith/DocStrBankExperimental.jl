```
Lift(f, (X₁, X₂ … Xₙ)) :: Query
```

`Lift`を使用すると、関数をクエリコンビネータとして利用できます。

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> Lift(+, (It.x, It.y))]
┼───┼
│ 3 │
```

`Lift`は、関数がクエリに対してブロードキャストされるときに暗黙的に使用されます。

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> (It.x .+ It.y)]
┼───┼
│ 3 │
```

`AbstractVector`を受け入れる関数は、複数のクエリで使用できます。

```jldoctest
julia> unitknot[sum.(Lift(1:3))]
┼───┼
│ 6 │
```

`AbstractVector`を返す関数は、複数のクエリになります。

```jldoctest
julia> unitknot[Lift((x='a', y='c')) >> Lift(:, (It.x, It.y))]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```
