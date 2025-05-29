```
rotate(mat::AbstractMatrix, α::Real; <keyword arguments>)
```

行列 `mat` を中心に角度 `α`（度単位）で回転させます。`rows` と `cols` が指定されていない場合、回転後の行列は元の行列と同じサイズになります。

# 引数

  * `mat`: 回転させる行列。
  * `α`: 度単位の角度。
  * `rows=nothing`: 回転後の行列の行数。
  * `cols=nothing`: 回転後の行列の列数。
  * `interpolation`: 補間戦略。デフォルトは `BilinearInterpolation` です。
