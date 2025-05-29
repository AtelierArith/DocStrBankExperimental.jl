```
intern(::Type{T}, s)
```

Intern `s` as if it were type `T`, converting it if required. Note that this will lead to unexpected behavour if the type of `s`, and `T`, do not have equivalent equality and hash functions (i.e. this is not safe if `hash(s) != hash(convert(T, s))`).
