```
showBand(Hamiltonian::Function; N::Int=51, labels::Bool=true, value::Bool=true, disp::Bool=false, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="Band")
```

この関数は、与えられたハミルトニアンのバンド構造プロットを生成します。

# 引数

  * `Hamiltonian::Function`: 波数パラメータ `k` を受け取り、対応するハミルトニアン行列を返すハミルトニアン関数。
  * `N::Int`: ブリルアンゾーン内のポイント数。デフォルトは51。
  * `labels::Bool`: 図のラベルを表示するかどうか。デフォルトは `true`。
  * `value::Bool`: 波数とエネルギーの値を行列形式で出力するかどうか。デフォルトは `true`。
  * `disp::Bool`: プロットを表示するかどうか。デフォルトは `false`。
  * `png::Bool`: プロットをPNGファイルとして保存するかどうか。デフォルトは `false`。
  * `pdf::Bool`: プロットをPDFファイルとして保存するかどうか。デフォルトは `false`。
  * `svg::Bool`: プロットをSVGファイルとして保存するかどうか。デフォルトは `false`。
  * `filename::String`: 保存するプロットのファイル名。デフォルトは "Band"。

# 例

```julia
julia> H(k) = SSH(k, (0.9, 1.0)) # $N \times N$ ハミルトニアン行列と波数パラメータ k
julia> showBand(H)
(k = -3.141592653589793:0.12566370614359174:3.141592653589793, Ene = [-0.09999999999999998 0.09999999999999998; -0.15554271964299698 0.15554271964299698; … ; -0.15554271964299698 0.15554271964299698; -0.09999999999999998 0.09999999999999998])
```
