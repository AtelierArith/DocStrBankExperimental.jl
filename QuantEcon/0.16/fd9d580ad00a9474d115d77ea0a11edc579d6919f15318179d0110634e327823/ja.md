動的計画法の問題を解決します。

##### パラメータ

  * `ddp::DiscreteDP` : モデルパラメータを含むオブジェクト
  * `method::Type{T<Algo}(VFI)`: 解法メソッドを指定する型名。受け入れ可能な引数は、値関数反復のための `VFI`、政策関数反復のための `PFI`、または修正政策関数反復のための `MPFI` です。
  * `;max_iter::Int(250)` : 最大反復回数
  * `;epsilon::Float64(1e-3)` : イプシロン最適性の値。`method` が `VFI` の場合のみ使用されます。
  * `;k::Int(20)` : 修正政策反復における部分政策評価の反復回数（他のメソッドには無関係です）。

##### 戻り値

  * `ddpr::DPSolveResult{Algo}` : `DPSolveResult` として表される最適化結果。詳細については `DPSolveResult` を参照してください。
