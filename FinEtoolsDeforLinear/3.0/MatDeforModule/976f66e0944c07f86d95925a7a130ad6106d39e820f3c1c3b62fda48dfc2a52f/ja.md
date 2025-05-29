```
tens4ikjl!(t::Array{T, 4}, A::FA, B::FB) where {T, FA, FB}
```

2つの2次テンソルのダイアディック積として4次テンソルを埋めます。

`i,j,k,l`成分は`t[i,j,k,l]=A(i,k)*B(j,l)`として与えられます。

!!! note



テンソルは累積されます。初期状態としてゼロに初期化する必要があります。

# 例

```
t = fill(0.0, 3, 3, 3, 3)
delta = (I, J) -> I == J ? 1.0 : 0.0
tens4ikjl!(t, delta, delta)
S = rand(3, 3)
@show transpose(S) 
tS = fill(0.0, 3, 3)
@show transpose(S) - tens4dot2!(tS, t, S)
```
