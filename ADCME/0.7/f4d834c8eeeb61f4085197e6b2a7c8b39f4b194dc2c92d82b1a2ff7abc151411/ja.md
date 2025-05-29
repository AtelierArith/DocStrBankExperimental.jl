```
test_gradients(f::Function, x0::Array{Float64, 1}; scale::Float64 = 1.0, showfig::Bool = true)
```

ベクトル関数 `f` の勾配をテストします: `y, J = f(x)` ここで `y` はスカラー出力で、`J` はベクトル勾配です。
