```
transform!(node::Node, args..., <keyword arguments>)
transform(node::Node, args..., <keyword arguments>)
```

MTG（`node`）をインプレース（`transform!`）またはコピー（`transform`）で、`args...`で指定された属性を追加します。

# 引数

  * `node::Node`: MTGノード（*例* `read_mtg()`によって返される全体のmtg）。
  * `args::Any`: 変換（詳細は参照）
  * <keyword arguments>:

      * `scale = nothing`: フィルタリングするスケール（保持するため）。通常は整数のタプルのようなもの。
      * `symbol = nothing`: フィルタリングするシンボル。通常は文字列のタプルのようなもの。
      * `link = nothing`: フィルタリングする前のノードとのリンク。通常は文字のタプルのようなもの。
      * `filter_fun = nothing`: ノードを入力として受け取る任意のフィルタリング関数、例：[`isleaf`](@ref)。
      * `ignore_nothing = false`: 指定された属性の`nothing`値を持つノードをフィルタリング（形式 :var_name => ... にのみ適用）。

# 戻り値

`transform!`: 何も返さず、（サブ）ツリーをインプレースで変異させます。`transform`: `node`の変異したコピー。

# 注意

注意してください、`transform`は`transform!`よりもはるかに遅いです。なぜなら、毎回全体のMTGのコピーを作成するからです。

# 詳細

この関数のインターフェースは、[`DataFrames.jl`](https://dataframes.juliadata.org/stable/)で使用されるものからインスパイアされていますが、MTGに適応されています。

提供される`args...`は以下の形式のいずれかであることができます：

1. `:var_name => :new_var_name`のペア。この形式は属性名をリネームするために使用されます。
2. `:var_name => function => :new_var_name`または

`[:var_name1, :var_name2...] => function => :new_var_name`のペア。変数はシンボルまたは文字列（またはそのベクター）として宣言され、関数に位置引数として渡されます。新しい属性名はオプションで、提供されない場合はソース列名と関数名を連結して自動的に生成されます。

3. `function => :new_var_name`の形式で、ノードに関数を適用し、結果を新しい属性に格納します。この形式は通常、祖先または子孫の値を検索する際に適用されます。
4. `function`の形式で、ノードに変異関数を適用し、出力を期待しません。

この形式は、ノードをすでに変異させる関数を使用する際に適応され、何も返す必要はありません。*例* [`branching_order!`](@ref)。

使用する形式に注意してください！形式2は、1つ以上のノード属性（== 変数）を入力として受け取る関数を期待しますが、形式3と4はノードを受け取る関数を期待します。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# transformを使用してすべてのノードに関数を適用できます（[`traverse!`](@ref)を使用するのと同じ）。
transform!(mtg,  node -> isleaf(node) ? println(node_id(x)," は葉です") : nothing)
node_5 は葉です
node_7 は葉です

# 別の属性に基づいて新しい変数を計算できます。たとえば、`Length`属性の値が提供されているかどうかを知るために、次のようにします：
transform!(mtg, :Length => isnothing)
# 値を確認するために、まず[`get_attributes`](@ref)を呼び出して新しい変数名を知ります：
get_attributes(mtg)
# そして、[`descendants`](@ref)を使用して値を取得します。
descendants(mtg, :Length_isnothing, self = true)
# またはDataFrame：
DataFrame(mtg, :Length_isnothing)

# 属性名を自分で設定することもできます：
transform!(mtg, :Length => isnothing => :no_length)
descendants(mtg, :no_length, self = true)

# 匿名関数を提供することもできます：
transform!(mtg, :Length => (x -> isnothing(x)) => :no_length)
descendants(mtg, :no_length, self = true)

# ノードに属性がない場合、`nothing`を返します。ほとんどの基本関数はこれをうまく処理しません。例：
transform!(mtg, :Length => log)
# これは、いくつかのノードが`Length`の値を持たないため、機能しません。
# `nothing`値を持つノードを自動的に削除するには、`ignore_nothing`を使用します：
transform!(mtg, :Length => log => :log_length, ignore_nothing = true)
descendants(mtg, :log_length, self = true)

# または、好みに応じて関数内で手動で処理することもできます：
transform!(mtg, :Length => (x -> x === nothing ? nothing : log(x)) => :log_length2)
descendants(mtg, :log_length2, self = true)

# 別の方法は、引数としてフィルタリング関数を提供することです：
transform!(mtg, :Length => log => :log_length, filter_fun = x -> x[:Length] !== nothing)

# 次のように、関数への入力として複数の属性を使用することもできます：
transform!(
    mtg,
    [:Width, :Length] => ((x, y) -> (x/2)^2 * π * y) => :volume,
    filter_fun = x -> x[:Length] !== nothing && x[:Width] !== nothing
)
descendants(mtg, :volume, self = true)

# `filter_fun`はノードをフィルタリングするので、ここではnode[:attribute]の表記を使用します。

# また、操作を連鎖させることができ、順次実行されるため、直前の命令で計算された変数を使用できます：
density = 0.6
transform!(
    mtg,
    [:Width, :Length] => ((x, y) -> (x/2)^2 * π * y) => :vol,
    :vol => (x -> x * density) => :biomass,
    filter_fun = x -> x[:Length] !== nothing && x[:Width] !== nothing
)
DataFrame(mtg, [:vol, :biomass])

# 変数を次のようにリネームすることもできます：
transform!(
    mtg,
    :biomass => :mass,
    filter_fun = x -> x[:Length] !== nothing && x[:Width] !== nothing
)
DataFrame(mtg, [:vol, :mass])

# 最後に、`function => :new_var`形式を使用して、祖先/子孫から変数を使用できます：
function get_mass_descendants(x)
    masses = descendants(x, :mass, ignore_nothing = true)
    if length(masses) == 0
        nothing
    else
        sum(masses)
    end
end

transform!(
    mtg,
    get_mass_descendants => :mass_beared
)
DataFrame(mtg, [:mass, :mass_beared])
```
