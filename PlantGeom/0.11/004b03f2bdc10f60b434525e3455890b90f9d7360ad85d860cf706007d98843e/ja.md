```
read_opf(file; attr_type = Dict, mtg_type = MutableNodeMTG)
```

OPFファイルを読み込み、MTGを返します。

# 引数

  * `file::String`: opfファイルへのパス。
  * `attr_type::DataType = Dict`: 各ノードの属性値を保持するために使用される型。
  * `mtg_type = MutableNodeMTG`: 各ノードのmtgエンコーディングを保持するために使用される型（*すなわち* link, symbol, index, scale）。詳細セクションを参照してください。
  * `read_id::Bool = true`: OPFからIDを読み込むか、動的に再計算するか。
  * `max_id::RefValue{Int64}=Ref(1)`: 最初のノードのID、`read_id==false`の場合。

# 詳細

`attr_type`は次のようにするべきです：

  * `NamedTuple`：mtgの属性を変更する予定がない場合、*例*：プロットや統計計算に使用するため...
  * `MutableNamedTuple`：属性値を変更する予定があるが、新しい属性を頻繁に追加する予定がない場合、*例*：属性値を再計算する...
  * `Dict`または類似のもの（*例*：`OrderedDict`）：属性を大幅に変更する予定がある場合、*例*：属性を頻繁に追加/削除する

`MultiScaleTreeGraph`パッケージは、`mtg_type`に対して2つの型を提供します。1つは不変（`NodeMTG`）、もう1つは可変（`MutableNodeMTG`）です。ノードのいくつかのmtgエンコーディングを変更する予定がある場合は`MutableNodeMTG`を使用し、何も変更したくない場合は`NodeMTG`を使用してください。こちらの方が速いはずです。

# 注意

さらなる詳細については、MTGパッケージのドキュメントからMTGフォーマットのドキュメントを参照してください。*例*：[MTGの概念](https://vezy.github.io/MultiScaleTreeGraph.jl/stable/the_mtg/mtg_concept/)。

# 返り値

MTGのルートノード。

# 例

```julia
using PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
# file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","coffee.opf")
opf = read_opf(file)
```
