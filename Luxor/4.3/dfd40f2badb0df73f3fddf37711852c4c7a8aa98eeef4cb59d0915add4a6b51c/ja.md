```
pointinverse(A::Point, centerpoint::Point, rad)
```

点Aの円`centerpoint`/`rad`に関する逆点`A′`を求めます。条件は次の通りです：

```julia
distance(centerpoint, A) * distance(centerpoint, A′) == rad^2
```

(return (true, A′) または (false, A))。
