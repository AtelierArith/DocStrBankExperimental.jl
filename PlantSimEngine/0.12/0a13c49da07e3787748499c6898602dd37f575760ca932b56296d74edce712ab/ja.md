```
status(m)
status(m::AbstractArray{<:ModelList})
status(m::AbstractDict{T,<:ModelList})
```

モデルリストのステータスを取得します。*すなわち* 入力（および出力）変数の状態です。

関連情報として [`is_initialized`](@ref) および [`to_initialize`](@ref) を参照してください。

# 例

```jldoctest
using PlantSimEngine

# 例のモデルとプロセスを含める:
using PlantSimEngine.Examples;

# モデルリストを作成
models = ModelList(
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model(),
    status = (var1=[15.0, 16.0], var2=0.3)
);

status(models)

# または1つの変数だけ:
status(models,:var1)


# またはi番目のタイムステップでのステータス:
status(models, 2)

# さらに簡単に:
models[:var1]
# 出力
2-element Vector{Float64}:
 15.0
 16.0
```
