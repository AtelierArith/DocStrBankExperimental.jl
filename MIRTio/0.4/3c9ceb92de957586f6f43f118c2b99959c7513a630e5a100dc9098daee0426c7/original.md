```
dat = loadrds(fid::IOStream, frames, frsize::Int, ncoil::Int;
              T::Type{<:Union{Int16,Int32}} = Int16)
```

Read multiple frames. Here, `frames` is an Int vector/array/range.

out

  * `dat::Array{Complex{T}}` `[frsize, ncoil, length(frames)]`
