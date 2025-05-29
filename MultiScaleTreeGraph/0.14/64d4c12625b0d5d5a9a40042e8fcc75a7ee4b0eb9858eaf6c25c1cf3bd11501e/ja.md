```
nleaves(node)
nleaves!(node)
```

ノードが持つ葉の総数、すなわち端末ノードの数を取得します。`nleaves!`は`nleaves`よりも高速ですが、結果を変数にキャッシュするため、より多くのメモリを使用します。`nleaves!`を呼び出した後は、[`clean_cache!`](@ref)を使用して一時変数をクリーンアップしてください。

# 例

```julia
# GitHubリポジトリからmtgをインポートする:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

nleaves!(mtg)

clean_cache!(mtg)
```
