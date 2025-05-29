```
biplot(table; kind=:form, dim=2, [aesthetics...])
```

与えられた `kind` の `table` のバイプロットを `dim` 次元空間で表示します。

バイプロットには4つの種類があります：

  * `:form`  - 形状パラメータ `α = 1` の標準バイプロット
  * `:cov`   - 形状パラメータ `α = 0` の標準バイプロット
  * `:rform` - `α = 1` の相対変動バイプロット
  * `:rcov`  - `α = 0` の相対変動バイプロット

# バイプロット属性

  * `kind` - バイプロットの種類（`:form`、`:cov`、`:rform` または `:rcov`）
  * `dim`  - 次元数 `dim ∈ {2,3}`（デフォルトは `2`）

# 美的属性

  * `axescolormap` - 主軸のカラーマップ（デフォルトはテーマのカラーマップ）
  * `dotcolormap`  - サンプルドットのカラーマップ（デフォルトはテーマのカラーマップ）
  * `fontsize`     - 軸とドットのフォントサイズ（デフォルトは `12`）
  * `axesbody`     - 主軸のボディのサイズ（`dim` に依存）
  * `axeshead`     - 主軸のヘッドのサイズ（`dim` に依存）
  * `axescolor`    - 主軸の色（デフォルトは `:black`）
  * `axeslabel`    - 主軸の名前（デフォルトは `x1,x2,...`）
  * `dotsize`      - サンプルドットのサイズ（`dim` に依存）
  * `dotcolor`     - サンプルドットの色（デフォルトは `:black`）
  * `dotlabel`     - サンプルドットの名前（デフォルトは `1:nobs`）
  * `showdots`     - ドットの名前を表示する（デフォルトは `true`）
  * `showlinks`    - 主軸間のリンクを表示する（デフォルトは `false`）

詳細は https://en.wikipedia.org/wiki/Biplot を参照してください。

## 参考文献

  * Gabriel, K. 1971. [The Biplot Graphic Display of Matrices with Application to Principal Component Analysis](https://www.jstor.org/stable/2334381)
  * Aitchison, J. & Greenacre, M. 2002. [Biplots of Compositional data](https://rss.onlinelibrary.wiley.com/doi/abs/10.1111/1467-9876.00275)
