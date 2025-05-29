```
ParamTable(type::Symbol,table;
location = nothing,
name = nothing,
grouptype = :unknown,
options = ParamOptions())
```

クレペロンCSVファイルを作成し、そのファイルの場所を返します。typeはテーブルのタイプを決定します：

  * `:single` は単一パラメータのテーブルを作成します
  * `:pair` はペアパラメータのテーブルを作成します
  * `:assoc` は関連パラメータのテーブルを作成します
  * `:group` は関連パラメータのテーブルを作成します

デフォルトでは、名前はランダムに生成され、テーブルは一時的なスクラッチスペース（Scratch.jlによって提供される）に保存されます。このスクラッチスペースは `Clapeyron.cleartemp!()` を使用してクリーンアップできます。

## 例：

```julia-repl
julia> data = (species = ["water"],Mw = [18.03]) #これはDict、名前付きタプル、またはTables.jl互換の任意のテーブルである可能性があります
(species = ["water"], Mw = [18.9])
julia> file = ParamTable(:single,data ,name="water_new_mw")
"C:\Users\user\.julia\scratchspaces\7c7805af-46cc-48c9-995b-ed0ed2dc909a\ParamTables\singledata_water_new_mw.csv"
julia> model = PCSAFT(["water","methanol"],userlocations = [file])
PCSAFT{BasicIdeal} with 2 components:
 "water"
 "methanol"
Contains parameters: Mw, segment, sigma,
epsilon, epsilon_assoc, bondvol
julia> model.params.Mw
SingleParam{Float64}("Mw") with 2 components:
 "water" => 18.9
 "methanol" => 32.042
```
