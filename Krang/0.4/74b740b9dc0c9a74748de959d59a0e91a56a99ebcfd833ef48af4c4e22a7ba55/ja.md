```julia
emission_inclination(pix::Krang.AbstractPixel, rs, νr)

```

発光傾斜は、傾斜 rs から発生した点のもので、その n 次の画像がスクリーン座標 (`α`, `β`) に表示されます。

# 引数

  * `pix` : ピクセル情報
  * `rs` : 発光半径
  * `νr` : 発光時の放射速度方向の符号。これは、ケース 3 およびケース 4 の測地線では常に正です。
