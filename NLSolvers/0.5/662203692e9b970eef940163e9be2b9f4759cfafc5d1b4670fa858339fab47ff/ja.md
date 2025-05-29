# ActiveBox

## コンストラクタ

```julia
    ActiveBox(; factorize = cholesky, epsilon = 1e-8)
```

`factorize` は制約付きヘッセ行列を因数分解する関数であり、`epsilon` は境界がほぼアクティブかどうかの閾値を決定します。詳細は [1] の式 (32) を参照してください。

## 説明

ActiveBox は境界制約付き凸最適化のための二次法です。これはアクティブセットであり、制約面の迅速な探索を可能にします。アクティブセットを考慮に入れた修正されたアルミホ線探索を採用しています。詳細は [1] に記載されています。

## 参考文献

  * 1. http://www.mit.edu/~dimitrib/ProjectedNewton.pdf
  * 2. Iterative Methods for Optimization https://archive.siam.org/books/textbooks/fr18_book.pdf
