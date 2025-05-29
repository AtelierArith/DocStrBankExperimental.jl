```
create_random_coordstates(nSamples, d, object=:magicSimplex, precision=10, roundToSteps::Int=0, nTriesMax=10000000)
```

`nSamples` $d^2$ 次元の CoordStates の配列を返します。

`object` を使用して、'magicSimplex' の場合は座標範囲を [0,1] に、'enclosurePolytope' の場合は [0, 1/d] に指定します。 `roundToSteps` が 0 より大きい場合、座標を範囲を `roundToSteps` 等しいサイズのセクションに分割する頂点に丸めます。 結果として得られる点の分布は一般的に均一ではないことに注意してください。
