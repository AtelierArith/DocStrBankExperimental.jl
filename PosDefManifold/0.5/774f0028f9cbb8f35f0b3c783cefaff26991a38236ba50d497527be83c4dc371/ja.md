```
function remove(X::Union{Vector, Matrix}, what::Union{Int, Vector{Int}};
				dims=1)
```

ベクトルから1つ以上の要素を削除するか、行列から1つ以上の列または行を削除します。

`X`が行列の場合、`dims`=1（デフォルト）は行を削除し、`dims`=2は列を削除します。

`X`がベクトルの場合、`dims`は影響しません。

第二引数は整数または整数のベクトルです。

**例**

```julia
a=randn(5)
b=remove(a, 2)
b=remove(a, collect(1:3)) # 行1から3を削除
A=randn(3, 3)
B=remove(A, 2)
B=remove(A, 2; dims=2)
A=randn(5, 5)
B=remove(A, collect(1:2:5)) # 行1、3、5を削除
C=remove(A, [1, 4])
A=randn(10, 10)
A=remove(A, [collect(2:3); collect(8:10)]; dims=2)
```
