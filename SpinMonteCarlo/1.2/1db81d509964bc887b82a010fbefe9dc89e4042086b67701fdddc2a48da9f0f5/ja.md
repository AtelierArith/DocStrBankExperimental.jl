```
loop_update!(model, param::Parameter)
loop_update!(model, T::Real,
             Jz::AbstractArray,
             Jxy::AbstractArray,
             Gamma:AbstractArray)
```

温度 `T = param["T"]` と結合定数 `Jz, Jxy` および横場 `Gamma` の下でループアルゴリズムによってスピン配置を更新します。
