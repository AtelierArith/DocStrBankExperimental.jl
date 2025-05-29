```
Deplanarize(PL::Plane,sol::AbstractODESolution; N::Int=500) -> Matrix
Deplanarize(PL::Plane,sol::AbstractODESolution, Ts::AbstractVector{<:Number}) -> Matrix
```

`sol`の2D出力を、`PL`に関連付けられた平面座標から`PL`の周囲空間の座標に変換します。
