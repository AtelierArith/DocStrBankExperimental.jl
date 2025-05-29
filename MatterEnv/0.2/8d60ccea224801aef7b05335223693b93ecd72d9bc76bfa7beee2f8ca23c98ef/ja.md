```
load_eigenval(filename::String="EIGENVAL", spin::Bool=false) -> Bands, Kpoints
```

EIGENVALファイルからバンド構造を読み込みます。

# 引数

  * `filename::String="EIGENVAL"`: 入力ファイルの名前
  * `spin::Bool=false`: スピンアップとスピンダウンを区別するかどうか

# 戻り値

  * `Bands`: 各k点におけるエネルギーの固有値
  * `Array{KPoint, 1}`: K点と重み
