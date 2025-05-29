```
read_meta(fn, group)
```

メタデータファイルを読み込みます。最初の行はヘッダーであると仮定され、行名はプロファイル名（セルバーコード）であると仮定されます。グループ情報は、ヘッダー名が `group` の列によって指定されます。`group` が見つからない場合は、2列目が使用されます。グループ化されたプロファイル名（ベクトルのベクトル）とグループ名を返します。

# 例

```jldoctest

julia> grp, nam = read_meta("meta.tsv", "Cluster")

julia> length(grp)
12

julia> length.(grp)
12-element Vector{Int64}:
   65
  512
 1057
  647
  654
  326
  680
  369
 1191
   46
  101
   80

julia> length(nam)
12
```
