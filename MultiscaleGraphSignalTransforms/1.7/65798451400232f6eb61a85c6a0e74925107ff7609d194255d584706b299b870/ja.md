```
function dmatrix_ldb_flatten(dmatrix::Array{Float64,3}...; dm::Symbol = :KLdivergence)
```

LDBメソッドを使用してdマトリックスをフラット化します。この関数が呼び出された後、サイズ(~, ~, 1)の行列を返します。

### 入力引数

  * `dmatrix::Array{Float64,3}`: 1つのクラスにおけるLDB展開係数の行列。
  * `dm::Symbol`: 判別測度。オプション: `:KLdivergence`（デフォルト）、`:Jdivergence`、`:l1`、`:l2`、および `:Hellinger`。

### 使用例:

`dmatrix_ldb_flatten(dmatrix1, dmatrix2, dmatrix3)`、各引数は信号のクラスの展開係数行列です。デフォルトの判別測度KLダイバージェンスを使用してこれらの行列をフラット化します。言い換えれば、これらの展開係数行列を計算し、相互の「統計的距離」を合計することによってフラット化します。
