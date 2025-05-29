```
select_lifetime_polynomial(X_data::Vector{NTuple{d,Float64}}, Y_data::Vector{Float64},
                           debias_order::Int=0) where {d}
```

ポリノミアル推定を使用して（デバイアスされた）モンドリアンランダムフォレストのライフタイムパラメータを選択します。

# 例

```julia
data = generate_uniform_data_uniform_errors(2, 50)
X_data = data["X"]
Y_data= data["Y"]
debias_order = 0
lambda = select_lifetime_polynomial(X_data, Y_data, debias_order)
```
