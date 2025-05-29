```
init!(it::OptISTA, b::vecT
          ; A=solver.A
          , x::vecT=similar(b,0)
          , t::Float64=1.0) where T
```

（再）初期化する OptISTA イテレータ
