```
dat = loadrds(fid::IOStream, frames, frsize::Int, ncoil::Int;
              T::Type{<:Union{Int16,Int32}} = Int16)
```

複数のフレームを読み込みます。ここで、`frames` は Int ベクター/配列/範囲です。

out

  * `dat::Array{Complex{T}}` `[frsize, ncoil, length(frames)]`
