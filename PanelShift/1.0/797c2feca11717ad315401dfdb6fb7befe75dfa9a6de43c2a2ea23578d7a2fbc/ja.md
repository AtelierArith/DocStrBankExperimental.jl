```
tlead(tv, xv, n = oneunit(tv[1] - tv[1]); checksorted=true)
```

時間ベクトル `tv` に関して、ベクトル `xv` を `n` だけ前方にリードします。`tv` にギャップがあっても構いません。

`n` の型は、算術演算のために `tv` と一貫性がある必要があります。例えば、`tv` が日付ベクトルである場合、`n` は `Period` である必要があります。例えば `Day(2)` のように。デフォルトでは、`n` は `tv` の単位差として設定されます。

時間ベクトル `tv` は厳密に増加している必要があります。この要件はデフォルトでチェックされます。ユーザーは、`checksorted=false` を設定することで、パフォーマンスに敏感なコードのためにこの動作をオフにすることができます。

# 例

```jldoctest
julia> tlead([1;2;4], [4,5,6], 1)
3-element Vector{Union{Missing, Int64}}:
 5
  missing
  missing
```

```jldoctest
julia> tlead([Date(2020);Date(2022);Date(2024)], [4,5,6], Year(2))
3-element Vector{Union{Missing, Int64}}:
 5
 6
  missing
```

`tlag`、`tshift` も参照してください。
