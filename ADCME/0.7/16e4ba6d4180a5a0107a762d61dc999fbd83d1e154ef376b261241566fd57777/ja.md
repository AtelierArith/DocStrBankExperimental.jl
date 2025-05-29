```
test_hessian(f::Function, x0::Array{Float64, 1}; scale::Float64 = 1.0)
```

スカラー関数 `f` のヘッセ行列をテストします: `g, H = f(x)` ここで `y` はスカラー出力、`g` はベクトル勾配出力、`H` はヘッセ行列です。
