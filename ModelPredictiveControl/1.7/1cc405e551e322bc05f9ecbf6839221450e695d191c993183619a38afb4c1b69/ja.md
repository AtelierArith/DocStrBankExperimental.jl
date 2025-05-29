```
evaloutput(model::SimModel, d=[]) -> y
```

`SimModel`の出力`y`を`model.x0`の状態と測定された外乱`d`から評価します。

現在の時間ステップでの`model`の出力$\mathbf{y}(k)$を返します。[`SimModel`](@ref)オブジェクトを呼び出すと、この`evaloutput`メソッドが呼び出されます。

# 例

```jldoctest
julia> model = setop!(LinModel(tf(2, [10, 1]), 5.0), yop=[20]);

julia> y = evaloutput(model)
1-element Vector{Float64}:
 20.0
```
