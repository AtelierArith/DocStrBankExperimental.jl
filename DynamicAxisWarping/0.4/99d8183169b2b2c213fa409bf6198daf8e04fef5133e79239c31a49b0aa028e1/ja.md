```
inds = align_signals(s::AbstractVector{<:AbstractArray}, master = argmax(length.(s)); method = :dtw, output=:indices)
```

`s[i][inds[i]]` が `s[master]` に最適に整列するようなインデックスのセットを計算します。`inds` のすべての要素は同じ長さになります。

# 引数:

  * `s`: 整列する信号のベクトル
  * `master`: 参照として使用される信号のインデックス。すべての他の信号はこの信号に整列されます。
  * `method`: `:dtw` は `s[master]` と `s[i]` の間の dtw からのワーピングパスを使用します。`:xcorr` は `DSP.finddelay` を使用し、内部で信号間の相互相関を計算しますが、これによりわずかな不整合が生じることがよくあります。
  * `output`: デフォルトは整列インデックスを出力することですが、整列された `:signals` 自体を出力することもできます。
