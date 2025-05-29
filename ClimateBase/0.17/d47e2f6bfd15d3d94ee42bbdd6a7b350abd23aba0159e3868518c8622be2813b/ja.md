```
lonlatfirst(A::ClimArray, args...) → B
```

`A`の次元を入れ替えて、新しい配列`B`を作成します。`B`は最初の次元が経度、2番目の次元が緯度で、残りの次元は`A`に従います（ほとんどのプロット関数に便利です）。オプションの追加次元は`args...`として指定でき、残りの次元の特定の順序を指定します。

例:

```julia
B = lonlatfirst(A)
C = lonlatfirst(A, Time)
```
