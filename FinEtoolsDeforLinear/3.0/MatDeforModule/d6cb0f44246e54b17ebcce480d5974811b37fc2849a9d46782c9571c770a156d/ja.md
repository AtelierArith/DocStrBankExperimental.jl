```
tens4iljk!(t::Array{T, 4}, A::FA, B::FB) where {T, FA, FB}
```

2次のテンソル2つのダイアディック積として4次のテンソルを埋めます。

`i,j,k,l`成分は`t[i,j,k,l]=A(i,l)*B(j,k)`として与えられます。

!!! note



テンソルは累積されます。初期状態としてゼロに初期化する必要があります。

# 例

```
t = fill(0.0, 3, 3, 3, 3)
delta = (I, J) -> I == J ? 1.0 : 0.0
tens4iljk!(t, delta, delta)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
@show S - tens4dot2!(tS, t, S)
```
