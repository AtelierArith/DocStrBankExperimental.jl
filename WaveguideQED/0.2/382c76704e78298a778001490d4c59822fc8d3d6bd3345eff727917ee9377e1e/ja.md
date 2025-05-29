```
twophoton(b::WaveguideBasis{T,1},ξ::Function,args...,norm=false) where {T}
```

# 引数

  * `b::WaveguideBasis{T,Nw}` は1つの波導のみを含み、インデックスは必要ありません。
  * 関数として与えられたξは `ξ(t1,t2,args...)` の形式に従う必要があります。ここで、`t1` と `t2` は入力時間です。
  * `args...`: ξが関数である場合に渡される追加の引数。
  * `norm::Bool=false`: 結果の波束を正規化するかどうかを切り替えます。
