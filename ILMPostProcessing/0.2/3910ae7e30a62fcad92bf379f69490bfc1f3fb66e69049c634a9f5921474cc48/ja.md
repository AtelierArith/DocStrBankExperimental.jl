```
compute_FTLE!(FTLE, nx, ny, T, final_positions, dx, dy)
```

初期点の最終位置に基づいて、コロケーショングリッド上の`FTLE`フィールドを計算します。

基礎となる数学の詳細は、https://shaddenlab.berkeley.edu/uploads/LCS-tutorial/computation.html にあります。各グリッドポイントについて、まず2点中心差分を使用して流れマップの勾配を計算します。次に、2 x 2勾配行列の最大固有値を計算します。最後に、固有値を使用してFTLE値を計算します。

# 引数

  * `FTLE`: 空の2D配列（すなわち、`FTLE = zeros(Float64, ny - 2, nx - 2)`）、`nx - 2`および`ny - 2`は中心差分公式の境界点を考慮しています
  * `nx`: x方向のグリッドポイントの数
  * `ny`: y方向のグリッドポイントの数
  * `T`: 積分時間の長さ
  * `final_positions`: IVPの解
  * `dx`: x方向の初期グリッドの間隔
  * `dy`: y方向の初期グリッドの間隔
