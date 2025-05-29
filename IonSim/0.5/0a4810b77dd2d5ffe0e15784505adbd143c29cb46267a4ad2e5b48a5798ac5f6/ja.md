```
pointing!(laser::Laser, p::Vector{Tuple{T1, T2}} where T1<:Int where T2<:Real)
```

`laser`の指向を`p`で設定します。`length(p)`は`laser`を含む`Chamber`内のイオンの数と等しくなければなりません。
