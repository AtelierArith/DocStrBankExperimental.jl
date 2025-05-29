```
differentiate!(jacobian::VecOrMat{Float64}, tsg::TasmanianSG, x::AbstractVector{Float64})
```

は、補間関数の導関数（ヤコビアンまたは勾配ベクトル）を返します。

jacobian:  次元 X 出力の次元を持つベクトルまたは行列            各行は、vals の1列に対する補間関数の値に対応します tsg:  TasmanianSGのインスタンス x:  評価点である長さ次元のベクトル
