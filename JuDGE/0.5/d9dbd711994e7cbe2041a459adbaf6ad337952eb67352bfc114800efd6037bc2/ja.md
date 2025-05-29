```
UniformLeafProbabilities(tree::AbstractTree)
```

木に対して、この関数は葉ノードに対して一様分布があると仮定した場合に、木のノードを確率にマッピングする辞書を返します。

### 必要な引数

`tree` は確率分布が生成される木です。

### 例

```
probs = UniformLeafProbabilities(tree)
```
