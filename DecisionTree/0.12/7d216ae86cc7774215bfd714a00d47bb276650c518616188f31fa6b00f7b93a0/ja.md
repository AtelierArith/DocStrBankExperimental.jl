```
build_forest(model, labels, features, options...; keyword_options...)
```

`model`の更新版を返し、森に追加の`n_trees=options[2]`を追加します。ここで`options`と`keyword_options`は通常の`build_forest`メソッドと同様で、`model`引数は除外されます。

すべての`build_forest`呼び出しでトレーニングデータが同じであっても、ステップで木を追加することが一度にすべて追加することと同じであることを保証することは実際には不可能です。これは、乱数生成器が生成され使用される方法によるものです。しかし、他のすべての点において、これらのアプローチは同等です。

# 例

```
features, labels = load_data("iris")
features = float.(features)
labels = string.(labels)
```

呼び出し

```
model = build_forest(labels, features, 2, 200) # n_trees = 200
```

はおおよそ次のように等価です。

```
model1 = build_forest(labels, features, 2, 150) # n_trees = 150
model = build_forest(model1, labels, features, 2, 50) # n_trees = 50
```
