```
select_lifetime_gcv(lambdas::Vector{Float64}, n_trees::Int,
                    X_data::Vector{NTuple{d,Float64}}, Y_data::Vector{Float64},
                    debias_order::Int, n_subsample::Int) where {d}

一般化交差検証を使用して（デバイアスされた）モンドリアンランダムフォレストのライフタイムパラメータを選択します。

# 例

```

julia lambdas = collect(range(0.5, 10.0, step=0.5)) n*trees = 20 debias*order = 0 n*subsample = 40 data = generate*uniform*data*uniform*errors(2, 50) X*data = data["X"] Y*data= data["Y"] lambda = select*lifetime*gcv(lambdas, n*trees, X*data, Y*data, debias*order, n*subsample)

```

```
