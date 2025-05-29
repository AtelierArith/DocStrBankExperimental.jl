```
Yinyang()
```

Yinyangアルゴリズムの実装は、「Yufei Ding et al. 2015. Yinyang K-Means: A Drop-In Replacement of the Classic K-Means with Consistent Speedup. Proceedings of the 32nd International Conference on Machine Learning, ICML 2015, Lille, France, 6-11 July 2015」に基づいています。

一般的に、`Hamerly`アルゴリズムよりも優れており、`Elkan`アルゴリズムとほぼ同じ時間で、はるかに低いメモリ消費量を持っています。

`Yinyang`は以下の引数をサポートしています：`auto`: `Bool`、自動または手動のグルーピングを行うかどうかを示します。`group_size`: `Int`、グループごとの平均クラスタ数の推定値。低い数値は計算速度が速く、メモリ消費が高くなり、その逆も同様です。

`kmeans`関数で直接使用できます。

```julia
X = rand(30, 100_000)   # 30次元の100_000個のランダムポイント

# 3つのクラスタ、Yinyangアルゴリズム、デフォルトの7のgroup_size
kmeans(Yinyang(), X, 3)

# 以下は同等です
# 3つのクラスタ、group_sizeが10のYinyangアルゴリズム
kmeans(Yinyang(group_size = 10), X, 3)
kmeans(Yinyang(10), X, 3)

# ポイント数のサイズの1つのグループ
kmeans(Yinyang(auto = false), X, 3)
kmeans(Yinyang(false), X, 3)

# 中国語の表記も使用できます
kmeans(阴阳(), X, 3)
```
