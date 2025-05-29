DCTOp(T::Type, shape::Tuple, dcttype=2)

指定された入力配列に対してDCTを実行する`DCTOp <: AbstractLinearOperator`を返します。

# 引数:

  * `T::Type`       - 変換する配列の型
  * `shape::Tuple`  - 変換する配列のサイズ
  * `dcttype`       - DCTのタイプ（現在は`2`と`4`がサポートされています）
