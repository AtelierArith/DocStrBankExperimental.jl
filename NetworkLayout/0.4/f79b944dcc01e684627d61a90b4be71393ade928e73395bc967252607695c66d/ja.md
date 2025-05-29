```
LayoutIterator{T<:IterativeLayout,M<:AbstractMatrix}(algorithm, adj_matrix)
```

この型は、隣接行列と共に[`IterativeLayout`](@ref)を束ねて、ノードの位置をアイテムとする反復可能なオブジェクトを形成します。

## 例

```
for p in LayoutIterator(Stress(), adj_matrix)
    # 位置pを使って処理を行う
end
```
