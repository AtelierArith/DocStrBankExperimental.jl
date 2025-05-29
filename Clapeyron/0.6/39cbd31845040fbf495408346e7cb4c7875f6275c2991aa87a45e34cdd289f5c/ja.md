```
GroupParam
```

グループパラメータを保持する構造体。含まれるもの：

  * `components`: すべてのコンポーネントのリスト
  * `groups`: 各コンポーネントのグループ名のリスト
  * `grouptype`: 異なるグループモデルを区別するために使用される。
  * `i_groups`: 各コンポーネントのグループ数を含むリスト
  * `n_groups`: `i_groups`の各グループに対応する各グループのグループの重複度のリスト
  * `n_intragroups`: 各コンポーネントの各グループ間の接続グラフ（行列として）のリスト。
  * `flattenedgroups`: すべてのユニークなグループのリスト–パラメータはこのリストに対応する
  * `n_flattenedgroups`: `flattenedgroups`の各グループに対応するグループの重複度

`Vector{Tuple{String, Vector{Pair{String, Int64}}}}`を渡すことでグループパラメータを作成できます。例えば：

```julia-repl
julia> grouplist = [
           ("ethanol", ["CH3"=>1, "CH2"=>1, "OH"=>1]),
           ("nonadecanol", ["CH3"=>1, "CH2"=>18, "OH"=>1]),
           ("ibuprofen", ["CH3"=>3, "COOH"=>1, "aCCH"=>1, "aCCH2"=>1, "aCH"=>4])];
julia> groups = GroupParam(grouplist)
GroupParam(:unknown) with 3 components:
 "ethanol": "CH3" => 1, "CH2" => 1, "OH" => 1
 "nonadecanol": "CH3" => 1, "CH2" => 18, "OH" => 1
 "ibuprofen": "CH3" => 3, "COOH" => 1, "aCCH" => 1, "aCCH2" => 1, "aCH" => 4
julia> groups.flattenedgroups
7-element Vector{String}:
 "CH3"
 "CH2"
 "OH"
 "COOH"
 "aCCH"
 "aCCH2"
 "aCH"
julia> groups.i_groups
3-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 2, 3]
 [1, 4, 5, 6, 7]
julia> groups.n_groups
3-element Vector{Vector{Int64}}:
 [1, 1, 1]
 [1, 18, 1]
 [3, 1, 1, 1, 4]
julia> groups.n_flattenedgroups
 3-element Vector{Vector{Int64}}:
 [1, 1, 1, 0, 0, 0, 0]
 [1, 18, 1, 0, 0, 0, 0]
 [3, 0, 0, 1, 1, 1, 4]
```

グループデータを含むCSVがある場合、入力ベクトルの不足しているグループを自動的に照会するためにそれらを渡すこともできます：

```julia-repl
julia> grouplist = [
           "ethanol",
           ("nonadecanol", ["CH3"=>1, "CH2"=>18, "OH"=>1]),
           ("ibuprofen", ["CH3"=>3, "COOH"=>1, "aCCH"=>1, "aCCH2"=>1, "aCH"=>4])];
           julia> groups = GroupParam(grouplist, ["SAFT/SAFTgammaMie/SAFTgammaMie_groups.csv"])
           GroupParam with 3 components:
            "ethanol": "CH2OH" => 1, "CH3" => 1
            "nonadecanol": "CH3" => 1, "CH2" => 18, "OH" => 1
            "ibuprofen": "CH3" => 3, "COOH" => 1, "aCCH" => 1, "aCCH2" => 1, "aCH" => 4
```

この場合、`SAFTGammaMie`ファイルは二次グループ`CH2OH`をサポートしています。
