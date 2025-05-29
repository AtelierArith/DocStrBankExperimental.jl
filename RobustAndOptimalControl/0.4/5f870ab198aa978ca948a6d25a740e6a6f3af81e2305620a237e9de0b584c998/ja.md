```
show_construction([io::IO,] sys::LTISystem; name = "temp", letb = true)
```

`sys`を再構築するコードを`io`に出力します。

  * `letb`: trueの場合、コードはletブロックで囲まれます。

```@example
julia> sys = ss(tf(1, [1, 1]))
StateSpace{Continuous, Float64}
A = 
 -1.0
B = 
 1.0
C = 
 1.0
D = 
 0.0

連続時間状態空間モデル

julia> show_construction(sys, name="Jörgen")
Jörgen = let
    JörgenA = [-1.0;;]
    JörgenB = [1.0;;]
    JörgenC = [1.0;;]
    JörgenD = [0.0;;]
    ss(JörgenA, JörgenB, JörgenC, JörgenD)
end
```
