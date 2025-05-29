```
topic_tree(
    index::DocIndex, levels::AbstractVector{<:Union{Integer, AbstractString}};
    sorted::Bool = true)
```

`index`から提供された`levels`のトピックツリーを構築します。レベルはインデックスに存在する必要があります。例えば、最初に`build_cluster!`を実行してください。

# 引数

  * `index::DocIndex`: ドキュメントインデックス
  * `levels::AbstractVector{<:Union{Integer, AbstractString}}`: ツリーに含めるレベル、例えば`[4, 10, 20]`（これらはindex.topic_levelsに存在する必要があります）
  * `sorted::Bool`: 各トピックのドキュメント数によって子をソートするかどうか。デフォルトは`true`です。

# 例

```julia

# レベルk=4、k=10、k=20のトピックツリーを作成
root = topic_tree(index, [4, 10, 20])

# 表示する
print_tree(root)
# 例の出力
# "すべてのドキュメント (N: 10, シェア: 100.0%, レベル: root, トピックID: 0)"
# ├─ "トピック1 (N: 5, シェア: 50.0%, レベル: 4, トピックID: 1)"
# │  └─ "トピック1 (N: 5, シェア: 50.0%, レベル: 10, トピックID: 1)"
# ...
# └─ "トピック2 (N: 5, シェア: 50.0%, レベル: 4, トピックID: 2)"
#    └─ "トピック2 (N: 5, シェア: 50.0%, レベル: 10, トピックID: 2)"
# ...
```
