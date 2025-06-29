```
AbstractCamera
```

単一分子局在顕微鏡（SMLM）におけるすべてのカメラ実装のための抽象基本型。

# インターフェース要件

AbstractCameraの具体的なサブタイプは、以下を提供しなければなりません：

1. フィールド要件：

      * `pixel_edges_x::Vector{<:Real}`: x方向のピクセルエッジ位置のベクトル
      * `pixel_edges_y::Vector{<:Real}`: y方向のピクセルエッジ位置のベクトル
2. 単位：

      * すべてのエッジ位置は物理単位（マイクロメートル）でなければなりません
      * 原点 (0,0) はカメラの左上隅に対応します
      * N×Mピクセルのカメラの場合、N+1のxエッジとM+1のyエッジがあります
3. 座標規約：

      * ピクセル (1,1) は (pixel*size*x/2, pixel*size*y/2) マイクロメートルで中心にあります
      * エッジ位置は物理空間におけるピクセルの境界を定義します
      * 最初のエッジ位置は最初のピクセルの左/上エッジに対応します
      * 最後のエッジ位置は最後のピクセルの右/下エッジに対応します

# 注意事項

  * エッジ位置は単調増加でなければなりません
  * エッジの数は各次元のピクセル数よりも1つ多くなければなりません
  * ピクセルは通常サイズが均一ですが、これはインターフェースの要件ではありません
