```
read_box(file::XtcFile, frame::Integer, box::AbstractMatrix{T}) where {T <: Real}
```

# パラメータ

```
- file: "r"のためにすでにオープンされている必要があります
- frame: 1:nframesの範囲内である必要があります
- box: 次元(3, 3)で事前に割り当てられている必要があります
```
