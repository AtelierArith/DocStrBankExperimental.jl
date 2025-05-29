```
xfm_rotate!(outpoint::Vector{To}, xfm::Xform{Tx}, inpoint::Vector{Ti})
```

ボクセル座標ベクトルの長さ3で指定された点に、`Xform`構造体で指定された変換の回転成分を適用します。インプレースで行います。
