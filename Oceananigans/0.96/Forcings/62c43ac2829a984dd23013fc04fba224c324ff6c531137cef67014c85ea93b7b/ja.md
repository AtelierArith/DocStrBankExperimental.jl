```
LinearTarget{D}(intercept, gradient)
```

呼び出し可能なオブジェクトで、`intercept` と `gradient` を持つ線形ターゲット関数を返し、方向 `D` に沿って変化します。すなわち、

```
intercept + D * gradient
```

# 例

`z` に沿って変化し、`z=0` のときに `0` に等しく、勾配が 10⁻⁶ の線形ターゲット関数を作成します：

```julia
julia> target = LinearTarget{:z}(intercept=0, gradient=1e-6)
```
