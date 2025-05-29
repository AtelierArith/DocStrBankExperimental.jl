```
split_model(model::EoSModel)
split_model(model::EoSModel, splitter)
```

多成分システムのモデルを受け取り、モデルのベクトルを返します。結果は使用されるスプリッターによって異なります。

モデルはサブモデルのリストに分割でき、各サブモデルは元のモデルと同じタイプですが、異なる成分の組み合わせを持っています。

グループ寄与モデルも成分ベースで分割され、`split_model`はグループと成分ベース間の変換を自動的に処理します。

スプリッターは各サブモデルのインデックスのリストに過ぎず、有効なスプリッターは次のとおりです：

  * 整数のリスト：`split_model(model,[1,5,2])`は3つの純粋なモデルを返します。
  * 整数：`split_model(model,1)`は最初の成分に対応する1つのモデルを含むリストを返します。
  * リストのリスト：`split_model(model,[[1,2],[3])`は2つのモデルを含むリストを返し、最初のモデルは2つの成分を含み、2番目のモデルは純粋なモデルです。

デフォルトのスプリッターは`1:length(model)`で、すべての純粋なモデルを含むリストを返します。

## 例

```julia-repl
julia> model = MonomerIdeal(["methane","propane","butane"])
MonomerIdeal with 3 components:
 "methane"
 "propane"
 "butane"
Contains parameters: Mw, reference_state

julia> split_model(model)
3-element Vector{MonomerIdeal}:
 MonomerIdeal("methane")
 MonomerIdeal("propane")
 MonomerIdeal("butane")
 
julia> split_model(model,[[1,2],[3,1]])
2-element Vector{MonomerIdeal}:
 MonomerIdeal("methane", "propane")
 MonomerIdeal("butane", "methane")

julia> split_model(model,2)
1-element Vector{MonomerIdeal}:
 MonomerIdeal("propane")
```
