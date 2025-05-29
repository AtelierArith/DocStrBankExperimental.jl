```
compute_FTLE!(FTLE::ScalarGridData, final_x::ScalarGridData, final_y::ScalarGridData, dx::Real, dy::Real, T::Real)
```

初期点の最終位置に基づいて、コロケーショングリッド上の`FTLE`フィールドを計算します。

基礎となる数学の詳細は、https://shaddenlab.berkeley.edu/uploads/LCS-tutorial/computation.html にあります。各グリッドポイントについて、まず2点中心差分を使用して流れマップの勾配を計算します。次に、2 x 2勾配行列の最大固有値を計算します。最後に、固有値を使用してFTLE値を計算します。

# 引数

  * `FTLE`: `ScalarGridData`型のFTLEフィールドを保持します
  * `final_x`: `ScalarGridData`型の変形されたx位置
  * `final_y`: `ScalarGridData`型の変形されたy位置
  * `dx`: x方向の初期グリッドの間隔
  * `dy`: y方向の初期グリッドの間隔
  * `T`: 積分時間の長さ

```
