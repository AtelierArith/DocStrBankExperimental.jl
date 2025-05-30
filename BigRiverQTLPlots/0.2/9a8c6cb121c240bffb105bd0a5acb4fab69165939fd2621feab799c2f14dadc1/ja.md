get*plot*QTL_inputs(vLOD::Vector{<: AbstractFloat}, dfgInfo::DataFrame; 					chrColname::String="Chr", mbColname::String="Mb")

QTLプロットを生成するために必要な入力を取得します。

## 引数

  * `vLOD` は、各表現型の最大LODスコアの値とその対応するインデックスを含むベクトルです。
  * `dfpInfo` は、プローブセット、染色体名、Mb距離などの表現型情報を含むデータフレームです。
  * `dfgInfo` は、ローカス、cM距離、染色体名、Mb距離などの遺伝子型情報を含むデータフレームです。
  * `chrColname` は、染色体名を含む列の名前で、デフォルト名は "Chr" です。
  * `mbColname` は、メガベースDNA長を含む列の名前で、デフォルト名は "Mb" です。
