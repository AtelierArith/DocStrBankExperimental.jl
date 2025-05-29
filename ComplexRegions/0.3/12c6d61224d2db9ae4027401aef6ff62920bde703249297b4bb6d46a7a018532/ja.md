```
f(R::Union{AbstractDisk,AbstractHalfplane})
```

`R` が `AbstractDisk` または `AbstractHalfplane` の場合、`Möbius` マップ `f` の下でのその像を見つけます。結果もまた `AbstractDisk` または `AbstractHalfplane` です。

# 例

```julia-repl
julia> f = Möbius(Line(-1,1),Circle(0,1))
Möbius 変換:

   (1.0 + 0.9999999999999999im) z + (3.666666666666666 - 1.666666666666667im)
   ––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––
   (1.0 + 0.9999999999999999im) z + (-1.666666666666666 + 3.6666666666666665im)

julia> f(upperhalfplane)
Disk interior to:
   Circle(-5.55112e-17+2.22045e-16im,1.0)

julia> isapprox(ans,unitdisk)
true
```
