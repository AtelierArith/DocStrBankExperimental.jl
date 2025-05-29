```
KMeans(k; rate=LearningRate(.6))
```

`k` クラスターの近似 K-Means クラスタリング。

# 例

```
x = [randn() + 5i for i in rand(Bool, 10^6), j in 1:2]

o = fit!(KMeans(2, 2), eachrow(x))

sort!(o; rev=true)  # 観測数によってクラスターを並べ替え

classify(o, x[1])  # x[1] に最も近いクラスターのインデックスを返す
```
