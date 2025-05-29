モジュール CellArrays

`CellArray`という抽象配列のサブタイプをサポートし、単一の値ではなく論理配列を含むことができるセルを持つ配列を表します。データはGPU HPCアプリケーションに最適な方法で保存されます。

# 一般的な概要と例

https://github.com/omlins/CellArray.jl

# コンストラクタと型エイリアス

  * [`CellArray`](@ref)
  * [`CPUCellArray`](@ref)
  * `CuCellArray`（[`@define_CuCellArray`](@ref)を介して利用可能）
  * `ROCCellArray`（[`@define_ROCCellArray`](@ref)を介して利用可能）
  * `MtlCellArray`（[`@define_MtlCellArray`](@ref)を介して利用可能）

# 関数（標準のAbstractArray機能に追加）

  * [`cellsize`](@ref)
  * [`blocklength`](@ref)

コンストラクタや関数の説明を表示するには、それぞれ `?<constructorname>` または `?<functionname>` と入力してください。

!!! note "パフォーマンスノート"
    CellArrayのセルにレジスタに収まる以上のデータが含まれている場合、セルの値に個別にアクセスしてレジスタの圧力を軽減しない限り、Nvidia GPUでのパフォーマンスは最適から逸脱します。

