```
twophoton(b::WaveguideBasis{T,1},ξ::Matrix;norm=false) where {T}
```

# 引数

  * `b::WaveguideBasis{T,Nw}` は1つの波導のみを含み、インデックスは必要ありません。
  * ξ は次元 `(b.nsteps, b.nsteps)` の行列として与えられます。
  * `norm::Bool=false`: 結果の波束を正規化するかどうかを切り替えます。
