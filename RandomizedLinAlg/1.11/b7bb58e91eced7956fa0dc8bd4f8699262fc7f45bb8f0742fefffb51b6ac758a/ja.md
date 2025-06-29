```
rsvd(A, n, p=0)
```

行列 `A` の部分特異値分解をランダム化アルゴリズムを使用して計算します。

# 引数

`A`: 入力行列。

`n::Int`: 見つける特異値/ベクトルペアの数。

`p::Int=0`: 計算に含める追加のベクトルの数。

# 出力

`::SVD`: 特異値分解。

!!! warning "精度"
    このランダム化特異値分解のバリアントは最も一般的に見られる実装ですが、正確な計算には推奨されません。なぜなら、しばしば `n` 個の最大特異ペアを見つけるのに問題があり、必ずしも最大ではない `n` 個の大きな特異ペアを見つけることが多いためです。


# 実装ノート

この関数は `rrange` を呼び出し、ナイーブなランダム化範囲探索を使用して次元 `n` の部分空間の基底を計算します（[Halko2011] のアルゴリズム 4.1）。その後、`svd_restricted()` が呼び出され、ランダムに選択されたこの部分空間に制限された `A` の正確な SVD因子分解を計算します（[Halko2011] のアルゴリズム 5.1）。

または、任意のランダム化範囲探索アルゴリズムを使用して適切な部分空間を見つけ、その結果をその部分空間に制限された `SVD` を計算するルーチンのいずれかに渡すことで、自分自身のランダム化アルゴリズムを組み合わせて使用することもできます。
