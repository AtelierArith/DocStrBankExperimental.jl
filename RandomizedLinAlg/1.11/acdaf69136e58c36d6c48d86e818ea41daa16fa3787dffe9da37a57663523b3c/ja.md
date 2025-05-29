```
id(A, k, l)
```

行列 `A` の補間分解を計算して返します: A ≈ B * P

ここで:

  * `B` の列は `A` の列のサブセットです
  * `P` の列の一部は `k x k` 単位行列であり、`P` のエントリの絶対値は 2 を超えません、そして
  * ||B * P - A|| ≲ σ(A, k+1)、`A` の (`k+1`) 番目の特異値です。

# 引数

`A`: 因数分解する行列

`k::Int`: `B` に返す `A` の列の数

`l::Int`: 投影するランダムベクトルの長さ

# 出力

`(::Interpolative)`: 補間分解。

# 実装ノート

これは \cite{Liberty2007} と \cite{Cheng2005} で説明されているアルゴリズムのハッキーなバージョンです。前者は後者の因数分解 (3.1) を指します。しかし、補間分解を計算するためにこの因数分解を完全に計算する必要はありません。

代わりに、Y = R * A の最初の k 列のいくつかの順列を見つけ、A のサブセットを B に抽出し、次に B\A として P 行列を計算します。これにより、適切な最小二乗法を使用して自動的に P が計算されます。

ここで使用する近似は、真の列ピボットを使用するのではなく、Y の列ピボットを計算することです。これは列ピボット QR プロセスによって計算されるものです。

# 参考文献

\cite[Algorithm I]{Liberty2007}

```bibtex
@article{Cheng2005,
    author = {Cheng, H and Gimbutas, Z and Martinsson, P G and Rokhlin, V},
    doi = {10.1137/030602678},
    issn = {1064-8275},
    journal = {SIAM Journal on Scientific Computing},
    month = jan,
    number = {4},
    pages = {1389--1404},
    title = {On the Compression of Low Rank Matrices},
    volume = {26},
    year = {2005}
}
```
