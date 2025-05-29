```
read_box(file::DcdFile, frame::Integer, box::AbstractVector{T}) where {T <: Real}
```

# パラメータ

```
- file: "r" のためにすでにオープンされている必要があります
- frame: 1:nframes の範囲内である必要があります
- box: 次元 (6,) で事前に割り当てられている必要があります
```
