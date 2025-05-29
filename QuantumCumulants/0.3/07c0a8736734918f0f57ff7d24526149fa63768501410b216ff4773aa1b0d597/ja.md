```
change_index(term,from::Index,to::Index)
```

与えられた項内のすべての発生しているインデックスを、`from` インデックスから `to` インデックスに交換します。

# 例

```
change_index(σⱼ²¹,j,i) = σᵢ²¹

change_index(σⱼ²¹ * σᵢ¹²,j,i) = σᵢ²²
```
