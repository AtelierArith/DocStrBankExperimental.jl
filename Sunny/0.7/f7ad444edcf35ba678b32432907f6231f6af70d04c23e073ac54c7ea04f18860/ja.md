```
domain_average(f, cryst, qpts; rotations, weights)
```

逆格子空間の点 `qpts` に対して、離散的な `rotations` のセットの下で平均強度を計算します。回転は、グローバル座標系で、軸-角のペアまたは 3×3 の回転行列として与えることができます。各回転は `weights` の要素に従って重み付けされます。関数 `f` は回転された q-ポイントのリストを受け取り、[`intensities`](@ref) 計算を返す必要があります。

# 例

```julia
# グローバル z 軸の周りの 0, 120, および 240 度の回転
rotations = [([0,0,1], n*(2π/3)) for n in 0:2]
weights = [1, 1, 1]
res = domain_average(cryst, path; rotations, weights) do path_rotated
    intensities(swt, path_rotated; energies, kernel)
end
plot_intensities(res)
```
