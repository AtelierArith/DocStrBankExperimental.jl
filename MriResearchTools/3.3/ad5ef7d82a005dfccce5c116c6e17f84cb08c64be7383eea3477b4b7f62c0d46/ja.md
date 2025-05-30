```
header(v::NIVolume)
```

方向情報を含むヘッダーのコピーを返します。

# 例

```julia-repl
julia> vol = readmag("image.nii")
julia> hdr = header(vol)
julia> savenii(vol .+ 10, "vol10.nii"; header=hdr)
```
