```
has_preimage_with_preimage(f::MultTableGroupHom, g::MultTableGroupElem) -> (b::Bool, h::MultTableGroupElem)
```

$$
f
$$

の下で$g$に対する前像が存在するかどうかを返します。存在する場合、2番目の返り値は$f(h) = g$を満たす要素$h$です。
