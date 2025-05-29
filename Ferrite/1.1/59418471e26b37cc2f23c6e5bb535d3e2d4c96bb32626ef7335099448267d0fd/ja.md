```
function_symmetric_gradient(fe_v::AbstractValues, q_point::Int, u::AbstractVector, [dof_range])
```

関数の対称勾配を計算します。詳細は[`function_gradient`](@ref)を参照してください。`SymmetricTensor`を返します。

スカラー関数の対称勾配は次のように計算されます：$\left[ \mathbf{\nabla}  \mathbf{u}(\mathbf{x_q}) \right]^\text{sym} =  \sum\limits_{i = 1}^n  \frac{1}{2} \left[ \mathbf{\nabla} N_i (\mathbf{x}_q) \otimes \mathbf{u}_i + \mathbf{u}_i  \otimes  \mathbf{\nabla} N_i (\mathbf{x}_q) \right]$ ここで、$\mathbf{u}_i$は関数のノード値です。
