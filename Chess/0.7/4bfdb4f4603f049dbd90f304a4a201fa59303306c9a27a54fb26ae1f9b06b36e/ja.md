```
SquareDelta
```

2つの正方形の間のデルタまたはベクトルを表す型です。

`SquareDelta` 値は通常、定数 `DELTA_N`、`DELTA_S`、`DELTA_E`、`DELTA_W`、`DELTA_NW`、`DELTA_NE`、`DELTA_SW`、`DELTA_SE` のいずれかを通じて取得されるか、2つの正方形の値を引き算することによって得られます。

2つの `SquareDelta` を加算または減算したり、`SquareDelta` を整数スカラーで乗算したり、`SquareDelta` を `Square` に加算または減算することが可能です。

# 例

```julia-repl
julia> DELTA_N + DELTA_W == DELTA_NW
true

julia> SQ_D3 - SQ_C3 == DELTA_E
true

julia> SQ_G8 - 3 * DELTA_N
SQ_G5
```
