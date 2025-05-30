```
create_lefschetz_gf2(defcellbnd)
```

`GF(2)` 上にレフシェッツ複体を作成するには、その本質的なセルと境界を指定します。

入力引数 `defcellbnd` はベクトルのベクトルでなければなりません。各エントリ `defcellbnd[k]` は次の2つの形式のいずれかでなければなりません：

  * `[String, Int, String, String, ...]`：最初の `String` はセル `k` のラベルを含み、2番目のエントリにはその次元が続きます。残りのエントリは境界を構成するセルのラベルです。
  * `[String, Int]`：この短い形式は空の境界を持つセル用です。最初のエントリはセルラベルを示し、2番目はその次元です。

結果として得られるレフシェッツ複体のセルは、すべての発生するラベルの和集合に対応します。境界仕様にのみ現れるセルラベルは空の境界を持つと見なされ、上記の2番目の形式で別途指定する必要はありません。ただし、境界が空でない場合は、上記の最初の形式を使用してリストする必要があります。

# 例

```jldoctest
julia> defcellbnd = [["A",0], ["a",1,"B","C"], ["b",1,"B","C"]];

julia> push!(defcellbnd, ["c",1,"B","C"]);

julia> push!(defcellbnd, ["alpha",2,"b","c"]);

julia> lc = create_lefschetz_gf2(defcellbnd);

julia> lc.labels
7-element Vector{String}:
 "A"
 "B"
 "C"
 "a"
 "b"
 "c"
 "alpha"

julia> homology(lc)
3-element Vector{Int64}:
 2
 1
 0
```
