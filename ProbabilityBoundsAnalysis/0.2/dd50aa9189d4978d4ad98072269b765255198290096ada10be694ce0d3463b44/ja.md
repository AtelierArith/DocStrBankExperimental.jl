```
makepbox(x...)
```

入力の配列（例えば、区間や実数の配列）からpboxの配列を返します。

# 例

```jldoctest
julia> s = makepbox(interval(0,1))
Pbox: 	  ~  ( range=[0.0, 1.0], mean=[0.0, 1.0], var=[0.0, 0.25])

julia> array = [interval(0, 1), interval(0, 2), 3];

julia> s = makepbox.(array)
3-element Vector{pbox}:
 Pbox: 	  ~  ( range=[0.0, 1.0], mean=[0.0, 1.0], var=[0.0, 0.25])
 Pbox: 	  ~  ( range=[0.0, 2.0], mean=[0.0, 2.0], var=[0.0, 1.0])
 Pbox: 	  ~  ( range=3.0, mean=3.0, var=0.0)
```
