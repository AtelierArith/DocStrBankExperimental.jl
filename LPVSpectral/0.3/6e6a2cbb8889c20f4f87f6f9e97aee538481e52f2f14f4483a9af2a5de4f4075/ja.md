```
M = mel(fs::Real, nfft::Int; nmels::Int = 128, fmin::Real = 0f0, fmax::Real = fs/2f0)
```

メル行列 `M` を返します。`M*f` は、`f` がスペクトログラムのパワーのベクトルである場合、メルスペクトログラムになります。例えば、

```julia
M*abs2.(rfft(sound))
```
