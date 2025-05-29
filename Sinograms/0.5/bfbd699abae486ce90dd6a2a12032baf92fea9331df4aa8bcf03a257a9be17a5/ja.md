```
fbp_window(w::Window, N::Int ; T = Float32)
```

長さ `N` のアポダイジングウィンドウを作成し、`fftshift` します。

```jldoctest
julia> fbp_window(Window(Hamming()), 4)
4-element Vector{Float32}:
 1.0
 0.54
 0.0
 0.54
```
