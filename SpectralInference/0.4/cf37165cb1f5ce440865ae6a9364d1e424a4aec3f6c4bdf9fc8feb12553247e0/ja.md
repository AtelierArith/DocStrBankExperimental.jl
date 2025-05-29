```
squareform(d::AbstractVector, fillvalue=zero(eltype(d)))
squareform(d::AbstractVector, fillvalue=zero(eltype(d)))
```

もし `d` がベクトルであれば、`squareform` はそれが整数 `n` の `n` choose 2 の長さであるかをチェックし、その後 `d` の値で対称の正方行列の値を埋めます。

もし `d` が行列であれば、`squareform` はそれが正方行列であるかをチェックし、その後行列 `d` の下のオフダイアゴナルの値を列順でベクトルに埋めます。

`fillvalue` は生成されるベクトルまたは行列の初期値です。特に生成される行列では、対角線上の値になります。
