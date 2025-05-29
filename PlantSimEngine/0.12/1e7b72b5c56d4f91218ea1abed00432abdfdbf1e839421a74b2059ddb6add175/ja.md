```
add_organ!(node::MultiScaleTreeGraph.Node, sim_object, link, symbol, scale; index=0, id=MultiScaleTreeGraph.new_id(MultiScaleTreeGraph.get_root(node)), attributes=Dict{Symbol,Any}(), check=true)
```

グラフに器官を追加し、器官の（マルチスケール）変数の初期化を自動的に処理します。

この関数は、熱時間の関数として器官の出現を実装するモデルから呼び出されるべきです。

# 引数

  * `node`: 器官が追加されるノード（新しい器官の親器官）
  * `sim_object`: シミュレーションオブジェクト、例えばモデルの`extra`引数からの`GraphSimulation`オブジェクト。
  * `link`: 新しいノードと器官の間のリンクタイプ：

      * `"<"`: 新しいノードは親器官に従う
      * `"+"`: 新しいノードは親器官から分岐する
      * `"/"`: 新しいノードは親器官を分解する、*すなわち* スケールを変更する
  * `symbol`: 器官のシンボル、*例えば* `"Leaf"`
  * `scale`: 器官のスケール、*例えば* `2`。
  * `index`: 器官のインデックス、*例えば* `1`。インデックスは分岐順序や軸上の成長単位インデックスを簡単に識別するために使用される場合があります。これは一意のノード`id`とは異なります。
  * `id`: 新しいノードの一意のid。提供されない場合は、新しいidが生成されます。
  * `attributes`: 新しいノードの属性。提供されない場合は、空の辞書が使用されます。
  * `check`: 変数の初期化がチェックされるべきかどうかを示すブール値。`init_node_status!`に渡されます。

# 戻り値

  * `status`: 新しいノードのステータス

# 例

`Examples`モジュールの`ToyInternodeEmergence`例モデル（`examples`フォルダにもあります）や、使用例のための`test-mtg-dynamic.jl`テストファイルを参照してください。
