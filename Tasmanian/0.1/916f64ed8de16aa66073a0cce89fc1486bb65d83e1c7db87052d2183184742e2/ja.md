```
 evaluateBatch!(y::AbstractVecOrMat{Float64}, tsg::TasmanianSG, vals::AbstractVecOrMat{Float64})
```

関心のある点で補間関数を評価し、結果を `y` に設定します。

これは、グリッドが作成された後、値がロードされた後に呼び出す必要があります。

y: 出力の次元 X size(vals, 2) を持つベクトルまたは行列    各列は vals の1列に対する補間関数の値に対応します。

vals: 最初の次元が次元に等しいベクトルまたは行列       配列の各列は単一の要求された点です。
