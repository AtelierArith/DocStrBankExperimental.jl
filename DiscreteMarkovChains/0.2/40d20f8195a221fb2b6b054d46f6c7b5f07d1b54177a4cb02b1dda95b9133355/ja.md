```
first_passage_probabilities(x, t, i=missing, j=missing)
```

# 定義

これは、プロセスが時間 $t$ に状態 $j$ に初めて入る確率であり、プロセスが時間 0 に状態 $i$ から始まったことを前提としています。すなわち、$f^{(t)}_{i,j}$ です。`i` または `j` が指定されていない場合、`x` の状態空間における `i` と `j` のためのエントリ $f^{(t)}_{i,j}$ を持つ行列が返されます。

# なぜ遅いアルゴリズムを使用するのか？

`t` が必要に応じて象徴的であることができるようにするためです。つまり、象徴的数学ライブラリがこのライブラリを使用したい場合、問題は生じません。

# 引数

  * `x`: 何らかのマルコフ連鎖。
  * `t`: 初回通過確率を計算する時間。
  * `i`: プロセスが開始する状態。
  * `j`: プロセスが初めて到達しなければならない状態。

# 戻り値

`i` と `j` が指定されているかどうかに応じて、スカラー値または行列が返されます。

# 例

```jldoctest first_passage_probabilities
using DiscreteMarkovChains
T = [
    0.1 0.9;
    0.3 0.7;
]
X = DiscreteMarkovChain(T)

first_passage_probabilities(X, 2)

# 出力

2×2 Array{Float64,2}:
 0.27  0.09
 0.21  0.27
```

`X` にカスタム状態空間がある場合、`i` と `j` はその状態空間に含まれていなければなりません。

```jldoctest first_passage_probabilities
T = [
    0.1 0.9;
    0.3 0.7;
]
X = DiscreteMarkovChain(["Sunny", "Rainy"], T)

first_passage_probabilities(X, 2, "Sunny", "Rainy")

# 出力

0.09000000000000001
```

これは最初の例の (1, 2) エントリであることに注意してください。

# 参考文献

1. [University of Windsor](https://scholar.uwindsor.ca/cgi/viewcontent.cgi?article=1125&context=major-papers)
2. [Durham University](http://maths.dur.ac.uk/stats/courses/ProbMC2H/_files/handouts/1516MarkovChains2H.pdf)

```
