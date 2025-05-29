```
read_mtg(file, attr_type = Dict, mtg_type = MutableNodeMTG; sheet_name = nothing)
```

MTGファイルを読み込む

# 引数

  * `file::String`: MTGファイルへのパス。
  * `attr_type::DataType = Dict`: 各ノードの属性値を保持するために使用される型。
  * `mtg_type = MutableNodeMTG`: 各ノードのmtgエンコーディングを保持するために使用される型（*すなわち* link, symbol, index, scale）。詳細セクションを参照してください。
  * `sheet_name = nothing`: `xlsx`または`xlsm`ファイルを読み込む場合のシート名。`nothing`の場合は最初のシートを読み込みます（デフォルトの動作）。

# 詳細

`attr_type`は次のようにするべきです：

  * `NamedTuple`：mtgの属性を変更する予定がない場合、*例* プロットや統計計算に使用するため...

  * `MutableNamedTuple`：属性値を変更する予定があるが、新しい属性を頻繁に追加する予定がない場合、*例* 属性値を再計算する...

  * `Dict`または類似のもの（*例* `OrderedDict`）：属性を大幅に変更する予定がある場合、*例* 属性を頻繁に追加/削除する

`MultiScaleTreeGraph`パッケージは、`mtg_type`に対して2つの型を提供します。1つは不変（[`NodeMTG`](@ref)）、もう1つは可変（[`MutableNodeMTG`](@ref)）です。ノードのいくつかのmtgエンコーディングを変更する予定がある場合は[`MutableNodeMTG`](@ref)を使用し、何も変更したくない場合は[`NodeMTG`](@ref)を使用してください。こちらの方が速いはずです。

# 注意

さらなる詳細については、パッケージのドキュメントからMTGフォーマットのドキュメントを参照してください。*例* [MTGの概念](@ref)。

# 戻り値

MTGのルートノード。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# 必要に応じて属性を追加できるように別の`MutableNamedTuple`を使用する場合：
mtg = read_mtg(file,Dict);

# フィールドからExcelファイルから直接mtgを読み込むこともできます：
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","tree3h.xlsx")
mtg = read_mtg(file)
```
