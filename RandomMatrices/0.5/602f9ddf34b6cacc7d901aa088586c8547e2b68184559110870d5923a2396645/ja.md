確率的点過程によって定義されたランダムサンプルを計算します。これは、スペクトル因子化オブジェクト `L` によって定義されます。

入力:

```
`L`: N x N 行列の `Eigen` 因子化オブジェクト
```

出力:

```
`Y`: [1:N] のエントリを持つ `Vector{Int}`。
```

参考文献:

```
\cite{HKPV05} のアルゴリズム 18、\cite{KT12} のアルゴリズム 1 に記載されています。

@article{HKPV05,
    author = {Hough, J Ben and Krishnapur, Manjunath and Peres, Yuval and Vir'{a}g, B'{a}lint},
    doi = {10.1214/154957806000000078},
    journal = {Probability Surveys},
    pages = {206--229},
    title = {Determinantal Processes and Independence},
    volume = {3},
    year = {2005}
    archivePrefix = {arXiv},
    eprint = {0503110},
}

@article{KT12,
    author = {Kulesza, Alex and Taskar, Ben},
    doi = {10.1561/2200000044},
    journal = {Foundations and Trends in Machine Learning},
    number = {2-3},
    pages = {123--286},
    title = {Determinantal Point Processes for Machine Learning},
    volume = {5},
    year = {2012},
    archivePrefix = {arXiv},
    eprint = {1207.6083},
}

TODO: 直交性の喪失を確認する - Zelda Mariet からのヒント
```
