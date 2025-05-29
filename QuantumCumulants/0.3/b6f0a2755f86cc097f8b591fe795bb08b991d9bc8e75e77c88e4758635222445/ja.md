```
reorder(param,indexMapping)
```

与えられたインデックスマッピングに従って、指定された項（param）を再配置します。このインデックスマッピングは、与えられた項内でどの[`Index`](@ref)エンティティが等しくないかを指定します。reorder()は、結果として[`SpecialIndexedTerm`](@ref)を作成します。

# 例

```
reorder(σⱼ²¹ * σᵢ²¹,[(i,j)]) = σᵢ²¹ * σⱼ²¹

reorder(σⱼ²¹ * σᵢ²¹ * σⱼ¹²,[(i,j)]) = σᵢ²¹ * σⱼ²²
```
