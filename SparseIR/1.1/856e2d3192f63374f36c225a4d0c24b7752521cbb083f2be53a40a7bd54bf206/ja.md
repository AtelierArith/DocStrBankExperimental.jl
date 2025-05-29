```
FiniteTempBasisSet
```

IR基底とスパースサンプリングオブジェクトを保持するための型。

この型のオブジェクトは、フェルミオンとボソンのIR基底および関連するスパースサンプリングオブジェクトを保持します。

# フィールド

  * basis_f::FiniteTempBasis: フェルミオン基底
  * basis_b::FiniteTempBasis: ボソン基底
  * tau::Vector{Float64}: 虚時間領域のサンプリングポイント
  * wn_f::Vector{Int}: フェルミオン周波数のサンプリング
  * wn_b::Vector{Int}: ボソン周波数のサンプリング
  * smpl*tau*f::TauSampling: τおよびフェルミオンのためのスパースサンプリング
  * smpl*tau*b::TauSampling: τおよびボソンのためのスパースサンプリング
  * smpl*wn*f::MatsubaraSampling: マツバラ周波数およびフェルミオンのためのスパースサンプリング
  * smpl*wn*b::MatsubaraSampling: マツバラ周波数およびボソンのためのスパースサンプリング
  * sve_result::Tuple{PiecewiseLegendrePoly,Vector{Float64},PiecewiseLegendrePoly}: SVEの結果

# ゲッター

  * beta::Float64: 逆温度
  * ωmax::Float64: カットオフ周波数
