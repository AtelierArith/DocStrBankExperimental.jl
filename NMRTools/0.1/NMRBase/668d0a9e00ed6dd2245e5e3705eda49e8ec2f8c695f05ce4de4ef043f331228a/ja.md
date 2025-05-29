```
hasnonfrequencydimension(spectrum)
```

スペクトルに非周波数ドメイン次元が含まれている場合はtrueを返します。

# 例

```julia
julia> y2=loadnmr("exampledata/2D_HN/test.ft2");
julia> hasnonfrequencydimension(y2)
false
julia> y3=loadnmr("exampledata/pseudo3D_HN_R2/ft/test%03d.ft2");
julia> hasnonfrequencydimension(y3)
true
```
