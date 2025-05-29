```
lb, ub = getbounds(p::AbstractVector)
```

パラメータベクトル `p` の下限と上限のベクトルを返します。次のように境界を持つパラメータを作成します。

```
@parameters p [bounds=(-1, 1)]
```

さらに [`tunable_parameters`](@ref) や [`hasbounds`](@ref) を参照してください。
