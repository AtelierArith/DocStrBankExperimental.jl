```
pixwin(nside; pol=false)
```

# 引数:

  * `nside`: HEALPix 解像度パラメータ

# キーワード

  * `pol::Bool=false`: true の場合、偏光ピクセルウィンドウも返す

# 返り値:

  * `Vector{Float64}` ピクセルウィンドウ関数。`pol=true` の場合、温度と偏光のピクセルウィンドウのタプルを返す。

# 例

```julia-repl
julia> pixwin(4)
17-element Vector{Float64}:
 1.0000000000020606
 0.9942340766588788
 ⋮
 0.4222841034207188
```
