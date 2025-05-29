```
write_frame(file::XtcFile, step::Integer, time::Real, box::AbstractMatrix{S}, 
                coords::AbstractMatrix{T}) where {S, T <: Real}
```

# パラメータ

```
- file: "w" または "a" のためにすでに開かれている必要があります
- step: 積分ステップ 
- time: フレーム時間 (ps)
- box: 次元 (3, 3)
- coords: 次元 (3, natoms)
```
