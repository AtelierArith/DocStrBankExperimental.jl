```julia
plot_QTL(vLOD::Vector{<: AbstractFloat}, dfgInfo::DataFrame; 		chrColname::String="Chr", mbColname::String="Mb", 		thresholds::Vector{<: AbstractFloat}=[], kwargs...)

QTL分析のための散布図を生成します。

## 引数

  * `vLOD` はLODスコアの最大値を含むベクターです。
  * `dfgInfo` はローカス、cM距離、染色体名、Mb距離などの遺伝子型情報を含むデータフレームです。
  * `chrColname` は染色体名を含む列の名前で、デフォルト名は "Chr" です。
  * `mbColname` はメガベースDNA長を含む列の名前で、デフォルト名は "Mb" です。
  * `thresholds` はプロットのためのLODスコアのしきい値を含む <: AbstractFloat 数値ベクターです。

---

plot_QTL(scanresult::NamedTuple, dfgInfo::DataFrame; 		chrColname::String="Chr", mbColname::String="Mb",  		thresholds::Vector{<: AbstractFloat}=[], kwargs...)

QTL分析のための散布図を生成します。

## 引数

  * `scanresult` は `BulkLMM.jl` の `scan()` 関数から得られるNamedTupleオブジェクトです。
  * `dfgInfo` はローカス、cM距離、染色体名、Mb距離などの遺伝子型情報を含むデータフレームです。
  * `chrColname` は染色体名を含む列の名前で、デフォルト名は "Chr" です。
  * `mbColname` はメガベースDNA長を含む列の名前で、デフォルト名は "Mb" です。
  * `significance` はLODスコアのしきい値を推定するための有意水準を含む <: AbstractFloat 数値ベクターです。

`scanresult` に置換行列が含まれていない場合、元の最大LODスコアがプロットされ、`significance` ベクターの値が比較のためのしきい値として使用されます。
```
