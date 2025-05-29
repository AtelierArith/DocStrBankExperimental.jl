```
ConditionallyUniformProbabilities(tree::AbstractTree)
```

与えられた木に対して、この関数は木のノードを確率にマッピングする辞書を返します。これは、任意のノードの子供に対して条件付き一様確率があることを前提としています。

### 必要な引数

`tree` は、確率分布が生成される木です。

### 例

```
probs = ConditionallyUniformProbabilities(tree)
```
