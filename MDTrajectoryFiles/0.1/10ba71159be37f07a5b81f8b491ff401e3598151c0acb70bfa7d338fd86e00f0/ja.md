```
write_frame(file::DcdFile, box::AbstractVector{S}, 
                coords::AbstractMatrix{T}) where {S, T <: Real}
```

# パラメータ

```
- file: "w" または "a" 用に既に開かれている必要があります
- box 次元 (6, ) これらのパラメータの解釈はプログラムとバージョンによって異なります
- coords: 次元 (3, natoms) で事前に割り当てられている必要があります
```
