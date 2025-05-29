```
invmod(f::T, m::T) where T <: RingElem
```

$$
f
$$

の逆元を$m$を法として返します。つまり、`isone(mod(invmod(f,m)*f,m))`が`true`を返すことを意味します。

そのような逆元が存在しない場合、`NotInvertibleError`がスローされるべきです。
