### 説明

`momentmatrix` 関数は、`x` によって定義された推定問題のモーメント条件の行列を返します。モーメント条件は、一般化モーメント法 (GMM) や最尤推定 (MLE) など、さまざまな推定手法にとって重要です。

MLE の場合、モーメント行列はデータで評価された (擬似) 対数尤度関数のヘッセ行列の逆に対応します。GMM の場合、観測データで評価されたモーメント条件の行列を表します。

この関数は、ユーザー定義の型をサポートするように拡張でき、さまざまな推定手法に対する柔軟性を提供します。

### 使用法

```julia
momentmatrix(x) -> Matrix
momentmatrix(x, t) -> Matrix
momentmatrix!(x, y) -> Matrix
```

  * `momentmatrix(x)`: 推定問題 `x` のモーメント行列を返します。
  * `momentmatrix(x, t)`: パラメータが t に等しいときの推定問題 `x` のモーメント行列を返します。
  * `momentmatrix!(x, y)`: インプレースバージョンで、`x` に対して評価されたモーメント条件で行列 `y` を更新します。

返される行列は通常、サイズが `(obs x m)` であり、ここで `obs` は観測数を、`m` はモーメントの数を指します。ユーザーは、この関数をオーバーロードすることでカスタム型の独自のモーメント行列を定義できます。
