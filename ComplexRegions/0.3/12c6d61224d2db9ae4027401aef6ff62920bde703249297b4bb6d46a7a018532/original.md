```
f(R::Union{AbstractDisk,AbstractHalfplane})
```

If `R` is an `AbstractDisk` or an `AbstractHalfplane`, find its image under the `Möbius` map `f`. The result is also either an `AbstractDisk` or an `AbstractHalfplane`.

# Examples

```julia-repl
julia> f = Möbius(Line(-1,1),Circle(0,1))
Möbius transformation:

   (1.0 + 0.9999999999999999im) z + (3.666666666666666 - 1.666666666666667im)
   ––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––
   (1.0 + 0.9999999999999999im) z + (-1.666666666666666 + 3.6666666666666665im)

julia> f(upperhalfplane)
Disk interior to:
   Circle(-5.55112e-17+2.22045e-16im,1.0)

julia> isapprox(ans,unitdisk)
true
```
