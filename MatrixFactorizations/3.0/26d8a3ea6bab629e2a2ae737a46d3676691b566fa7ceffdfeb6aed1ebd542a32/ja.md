```
polar(A; algorithm::Symbol, maxiter, tol, verbose)
```

行列 `A` の極分解を計算します。

[`PolarDecomposition`](@ref) を返します。

引数:

`algorithm` (デフォルト: `:newton`) は次のいずれかです:

  * $$
    :newton
    $$

    : スケーリングされたニュートン法
  * $$
    :qdwh
    $$

    : QRベースの動的重み付きハレー法 (QDWH)
  * $$
    :halley
    $$

    : ハレー法
  * $$
    :schulz
    $$

    : ニュートン・シュルツ法
  * $$
    :hybrid
    $$

    : ハイブリッドニュートン法
  * $$
    :svd
    $$

    : SVD法

`maxiter` のデフォルトは 100; `tol` のデフォルトは `∛eps(t)`; `verbose` のデフォルトは `false` です。
