```
naca4(cam,pos,t[;np=20][,Zc=0.0+0.0im][,len=1.0]) -> Vector{Complex128}
```

1. NACA 4桁の翼型の頂点を生成します。弦長は1です。相対的なカンバーは`cam`で指定され、最大カンバーの位置（弦の割合として）は`pos`で指定され、相対的な厚さは`t`で指定されます。

オプションのパラメータ`np`は、上面または下面のポイント数を指定します。オプションのパラメータ`Zc`は頂点の平均位置を指定します（デフォルトでは原点に設定されています）。オプションのパラメータ`len`は弦長を指定します。

# 例

```jldoctest
julia> w = naca4(0.0,0.0,0.12);

julia> p = Polygon(w);
```
