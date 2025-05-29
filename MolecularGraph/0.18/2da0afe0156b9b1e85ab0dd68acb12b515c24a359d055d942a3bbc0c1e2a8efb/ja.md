```
substruct_matches(mol1, mol2; kwargs...) -> Iterator
```

`mol`が`query`を部分構造として持つ場合、`mol`と`query`の間のノードマッピングを生成する遅延イテレータを返します。

# オプション

  * `vmatch::Function`: セマンティック原子属性マッチングのための関数（デフォルト: `MolecularGraph.vmatch`）
  * `ematch::Function`: セマンティック結合属性マッチングのための関数（デフォルト: `MolecularGraph.ematch`）
  * `mandatory::Dict{Int,Int}`: 必須ノードマッピング（またはmatchtype=:edgeinducedの場合はエッジマッピング）
  * `forbidden::Dict{Int,Int}`: 禁止ノードマッピング（またはmatchtype=:edgeinducedの場合はエッジマッピング）
  * `timeout::Union{Int,Nothing}`: 指定された場合、時間が経過したときにvf2計算を中止し、空のイテレータを返します（デフォルト: 10秒）。
