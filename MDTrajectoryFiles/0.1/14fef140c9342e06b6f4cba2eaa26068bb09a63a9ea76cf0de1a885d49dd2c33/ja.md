```
read_atoms(file::XtcFile, frame::Integer, coords::AbstractMatrix{T}) where {T <: Real}
```

フレームの原子座標を読み取ります。

# パラメータ

  * file: "r" 用にすでにオープンされている必要があります
  * frame: 1:nframes の範囲内である必要があります
  * coords: 次元 (3, natoms) で事前に割り当てられている必要があります
