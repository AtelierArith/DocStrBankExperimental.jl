```
NLPModelMeta <: AbstractNLPModelMeta
```

最適化問題の主な特徴を表す合成型

```
optimize    obj(x)
subject to  lvar ≤    x    ≤ uvar
            lcon ≤ cons(x) ≤ ucon
```

ここで `x`        は `nvar` 次元のベクトル、       `obj`      は実数値の目的関数、       `cons`     はベクトル値の制約関数、       `optimize` は「最小化」または「最大化」のいずれかです。

ここで、`lvar`、`uvar`、`lcon` および `ucon` はベクトルです。それらの一部の要素は無限大であり、対応する境界または一般的な制約が存在しないことを示します。

---

```
NLPModelMeta(nvar::Integer; kwargs...)
NLPModelMeta(meta::AbstractNLPModelMeta; kwargs...)
```

`nvar` 変数を持つ `NLPModelMeta` を作成します。あるいは、別の `AbstractNLPModelMeta` から `NLPModelMeta` のコピーを作成します。以下のキーワード引数が受け入れられます：

  * `x0`: 初期推測
  * `lvar`: 下限のベクトル
  * `uvar`: 上限のベクトル
  * `nlvb`: 目的と制約の両方における非線形変数の数
  * `nlvo`: 目的における非線形変数の数（nlvbを含む）
  * `nlvc`: 制約における非線形変数の数（nlvbを含む）
  * `ncon`: 一般的な制約の数
  * `y0`: 初期ラグランジュ乗数
  * `lcon`: 制約下限のベクトル
  * `ucon`: 制約上限のベクトル
  * `nnzo`: 勾配における非ゼロの数
  * `nnzj`: スパースヤコビアンに非ゼロを格納するために必要な要素の数
  * `lin_nnzj`: 線形制約のスパースヤコビアンに非ゼロを格納するために必要な要素の数
  * `nln_nnzj`: 非線形制約のスパースヤコビアンに非ゼロを格納するために必要な要素の数
  * `nnzh`: スパースヘッセ行列に非ゼロを格納するために必要な要素の数
  * `lin`: 線形制約のインデックス
  * `minimize`: optimize == minimize の場合は true
  * `islp`: 問題が線形プログラムである場合は true
  * `name`: 問題名

`NLPModelMeta` には、上記の変数から計算される以下の属性も含まれています：

  * `nvar`: 変数の数
  * `ifix`: 固定変数のインデックス
  * `ilow`: 下限のみを持つ変数のインデックス
  * `iupp`: 上限のみを持つ変数のインデックス
  * `irng`: 下限と上限を持つ変数のインデックス（範囲）
  * `ifree`: 自由変数のインデックス
  * `iinf`: 明らかに実現不可能な境界のインデックス
  * `jfix`: 等式制約のインデックス
  * `jlow`: c(x) ≥ cl の形の制約のインデックス
  * `jupp`: c(x) ≤ cu の形の制約のインデックス
  * `jrng`: cl ≤ c(x) ≤ cu の形の制約のインデックス
  * `jfree`: 「自由」制約のインデックス（存在すべきではない）
  * `jinf`: 明らかに実現不可能な制約のインデックス
  * `nlin`: 線形制約の数
  * `nnln`: 非線形一般制約の数
  * `nln`: 非線形制約のインデックス
