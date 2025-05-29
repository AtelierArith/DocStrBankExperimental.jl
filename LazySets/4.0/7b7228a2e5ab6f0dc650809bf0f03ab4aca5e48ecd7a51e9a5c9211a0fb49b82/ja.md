```
minkowski_sum(P::AbstractPolyhedron, Q::AbstractPolyhedron;
              [backend]=nothing, [algorithm]=nothing, [prune]=true)
```

2つの多面体のミンコフスキー和を制約表現で計算します。

### 入力

  * `P`         – 制約表現の多面体
  * `Q`         – 制約表現の多面体
  * `backend`   – （オプション、デフォルト: `nothing`）多面体計算のバックエンド
  * `algorithm` – （オプション、デフォルト: `nothing`）変数を排除するためのアルゴリズム；利用可能なオプションは `Polyhedra.FourierMotzkin`、`Polyhedra.BlockElimination`、および `Polyhedra.ProjectGenerators`
  * `prune`     – （オプション、デフォルト: `true`）`true`の場合、冗長な制約を削除するための後処理を適用

### 出力

`P` と `Q` のミンコフスキー和に対応する H-表現の多面体。

### アルゴリズム

この関数は、[Kvasnica05](@citet)で詳述されているように、射影と変数排除による具体的なミンコフスキー和を実装しています。アイデアは、$P$ と $Q$ を *単純な H-表現* で書くと、すなわち、$P = \{x ∈ ℝ^n : Ax ≤ b \}$ および $Q = \{x ∈ ℝ^n : Cx ≤ d \}$ とすると、彼らのミンコフスキー和は多面体の最初の $n$ 次元座標への射影として見ることができます：

$$
    \begin{pmatrix} 0 & A \ C & -C \end{pmatrix} \binom{x}{y} ≤ \binom{b}{d}
$$

これは、$P ⊕ Q$ が $x = y + z$ であり、$Ay ≤ b$ および $Cz ≤ d$ となる点の集合に対応することに注意することで確認できます。したがって、$Ay ≤ b$ および $C(x-y) ≤ d$ が成り立ち、上記の不等式は $2n$ 次元空間 $\binom{x}{y}$ を考慮することで導かれます。$2n$ から $n$ 変数への削減は、次に説明する排除アルゴリズムを使用して行われます。

変数の排除は、変数排除のために `CDDLib` を使用する多面体ライブラリ `Polyhedra` に依存しています。利用可能なアルゴリズムは次のとおりです：

  * `Polyhedra.FourierMotzkin`    – H-表現を計算し、それに Fourier-Motzkin 排除アルゴリズムを適用することによる射影
  * `Polyhedra.BlockElimination`  – H-表現を計算し、それにブロック排除アルゴリズムを適用することによる射影
  * `Polyhedra.ProjectGenerators` – V-表現を計算することによる射影

```
