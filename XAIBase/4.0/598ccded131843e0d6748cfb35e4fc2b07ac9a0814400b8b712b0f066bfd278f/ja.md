```
MaxActivationSelector()
```

出力セレクタは、最も高い活性化を持つ出力を選択します。

## 注意

XAIBaseは、バッチ次元が出力の最後の次元であると仮定します。

## 例

```julia-repl
julia> output = rand(3, 3)
3×3 Matrix{Float64}:
 0.411871  0.313366  0.13402
 0.885562  0.136938  0.465622
 0.498235  0.627209  0.298911

julia> output_selector = MaxActivationSelector()
 MaxActivationSelector()

julia> output_selector(output)
 3-element Vector{CartesianIndex{2}}:
  CartesianIndex(2, 1)
  CartesianIndex(3, 2)
  CartesianIndex(2, 3)
```
