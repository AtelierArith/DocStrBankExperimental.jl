```
Coreset()
```

Coresetアルゴリズムの実装で、"Lucic, Mario & Bachem, Olivier & Krause, Andreas. (2015). Strong Coresets for Hard and Soft Bregman Clustering with Applications to Exponential Family Mixtures."に基づいています。

`Coreset`は以下の引数をサポートしています：

  * `m`: デフォルトは100、サブサンプルサイズ
  * `alg`: デフォルトは`Lloyd()`、サンプルをクラスタリングするために使用されるアルゴリズム

これは`kmeans`関数で直接使用できます。

```julia
X = rand(30, 100_000)   # 30次元の100_000個のランダムポイント

# 3つのクラスタ、デフォルトのLloydアルゴリズムと100のサブサンプルを使用したCoresetアルゴリズム
kmeans(Coreset(), X, 3)

# 3つのクラスタ、Hamerlyアルゴリズムと500のサブサンプルを使用したCoresetアルゴリズム
kmeans(Coreset(m = 500, alg = Hamerly()), X, 3)
kmeans(Coreset(500, Hamerly()), X, 3)

# 代わりに、サブサンプルサイズまたはアルゴリズムのみを定義するための短い形式を使用できます
kmeans(Coreset(500), X, 3) # サイズ500のサンプル、Lloydクラスタリングアルゴリズム
kmeans(Coreset(Hamerly()), X, 3) # サイズ100のサンプル、Hamerlyクラスタリングアルゴリズム
```
