```
GaussianMask{D}(center, width)
```

呼び出し可能なオブジェクトで、`center`を中心とし、`width`を持ち、方向`D`に沿って変化するガウスマスキング関数を返します。すなわち、

```
exp(-(D - center)^2 / (2 * width^2))
```

# 例

`z=0`を中心とし、幅`1`メートルのガウスマスクを作成します。

```julia
julia> mask = GaussianMask{:z}(center=0, width=1)
```
