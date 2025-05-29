```
ck45()
```

4次5段低ストレージCarpenter/Kennedyルンゲクッタ法の係数rka,rkb,rkcを返します。係数は残差、解、および局所時間を進化させます。例えば、

# 例

```julia
for i in eachindex(rk4a, rk4b)
    @. res = rk4a[i] * res + dt * rhs # i = RKステージ
    @. u  += rk4b[i] * res
end
```
