```
ftest(mod::LinearModel)
```

モデル `mod` が帰無モデル（すなわち、切片のみを含むモデル）よりも有意に適合しているかどうかを判断するためにF検定を実行します。

```jldoctest; setup = :(using DataFrames, GLM)
julia> dat = DataFrame(Result=[1.1, 1.2, 1, 2.2, 1.9, 2, 0.9, 1, 1, 2.2, 2, 2],
                       Treatment=[1, 1, 1, 2, 2, 2, 1, 1, 1, 2, 2, 2]);


julia> model = lm(@formula(Result ~ 1 + Treatment), dat);


julia> ftest(model.model)
帰無モデルに対するF検定:
F統計量: 241.62、観測数12、自由度1、p値: <1e-07
```
