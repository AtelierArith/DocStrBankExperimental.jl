```
 evaluateBatch(tsg::TasmanianSG, vals::AbstractVecOrMat{Float64})
```

は、関心のある点で補間関数を評価し、結果を返します。

これは、グリッドが作成され、値がロードされた後に呼び出す必要があります。

vals: 最初の次元が次元に等しいベクトルまたは行列       配列の各列は、要求された単一の点です。

出力: 次元が outputs X size(vals, 2) のベクトルまたは行列         各列は、vals の1列に対する補間関数の値に対応します。
