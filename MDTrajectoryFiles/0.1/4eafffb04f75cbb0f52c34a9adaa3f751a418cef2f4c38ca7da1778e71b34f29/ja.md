```
read_atoms(file::DcdFile, frame::Integer, coords::AbstractMatrix{T}) where {T <: Real}
```

フレームの原子座標を読み込みます。

# パラメータ

  * file: "r" のためにすでにオープンされている必要があります
  * frame: 1:nframes の範囲内である必要があります
  * coords: (3, natoms) の次元で事前に割り当てられている必要があります
