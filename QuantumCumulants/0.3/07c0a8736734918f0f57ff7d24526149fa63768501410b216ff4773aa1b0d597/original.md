```
change_index(term,from::Index,to::Index)
```

Exchanges all occuring indices inside the given term, that are equal to the `from` to the `to` index.

# Examples

```
change_index(σⱼ²¹,j,i) = σᵢ²¹

change_index(σⱼ²¹ * σᵢ¹²,j,i) = σᵢ²²
```
