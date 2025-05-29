```
eachindval(is::Index...)
eachindval(is::Tuple{Vararg{Index}})
```

指定された `Index` オブジェクトの次元に対する直交インデックスに対応する Index=>value ペアのイテレータを作成します。

# 例

```julia
i = Index(3; tags="i")
j = Index(2; tags="j")
T = random_itensor(j, i)
for iv in eachindval(i, j)
  @show T[iv...]
end
```
