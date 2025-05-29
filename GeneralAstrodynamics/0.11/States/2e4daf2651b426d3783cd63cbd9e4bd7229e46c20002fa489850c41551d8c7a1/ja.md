```julia
mutable struct CartesianState{F, LU, TU, AU} <: GeneralAstrodynamics.States.StateVector{F, LU, TU, AU, (x = 1, y = 2, z = 3, ẋ = 4, ẏ = 5, ż = 6, r = 1:3, v = 4:6)}
```

長さ6のカートesian状態ベクトル。内部ではデータを格納するために`MVector`と`LVector`を使用します。データは`x, y, z, ẋ, ẏ, ż, r, v`というラベルを介してアクセス可能であり、`r`は`x,y,z`にアクセスし、`v`は`ẋ, ẏ, ż`にアクセスします。
