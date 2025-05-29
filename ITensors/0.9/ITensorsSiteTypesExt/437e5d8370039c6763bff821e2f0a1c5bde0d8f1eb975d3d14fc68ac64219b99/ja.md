```
onehot(ivs...)
setelt(ivs...)
onehot(::Type, ivs...)
setelt(::Type, ivs...)
```

指定された値を1に設定し、それ以外はすべてゼロのITensorを作成します。

# 例

```julia
i = Index(2,"i")
A = onehot(i=>2)
# A[i=>2] == 1, 他のすべての要素はゼロ

# 要素の型を指定
A = onehot(Float32, i=>2)

j = Index(3,"j")
B = onehot(i=>1,j=>3)
# B[i=>1,j=>3] == 1, 他のすべての要素はゼロ
```
