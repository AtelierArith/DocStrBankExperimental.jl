```
単一パラメータを持つ毒物動態モデルを解く

$\frac{dx(t)}{dt} = k_d (conc(t) - x(t))$
```

**フィールド**     - `tps` – 時間ベクトル     - `conc` – 暴露ベクトル     - `kd` – パラメータ、スカラー

`Array{Float64,1}` のタプルを返し、`tps` と同じ長さであること。

# 例

```julia
julia> myTK = runTK([0,1,2,3], [0,1,20,2], 0.5);
julia> myTK.TK
4-element Array{Float64,1}:
 0.0
 0.21800446293645104
 4.570824232907027
 6.801199145490319
```
