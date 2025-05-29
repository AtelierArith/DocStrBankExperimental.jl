```
y2σs(y, ms::MassTuple; k::Int = last(findmin(Tuple(ms))))
```

変数のペアを平方質量の平面に線形変換を使用してマッピングします。値 [0,1] は平方質量変数の物理的限界に対応します。物理的な値

## 引数

  * `y` : 数のペア
  * `ms` : `MassTuple` としてのシステムの質量、`ThreeBodyMasses` を参照してください。
  * `k` : 変数が生成されないインデックス。デフォルトでは、関数はダリッツプロットが平方フィッティングボックスに最も近い形状を持つ座標を選択します。

## 戻り値

  * 平方質量を持つ `MandelstamTuple` のインスタンス。

DecayChainLS のドキュメント文字列：

## 例

100ポイントの位相空間サンプルは次のように生成できます： ```julia data = let N = 100

# ランダム変数をダリッツにマップ

_data = mapslices(rand(N,2); dims=2) do xy y2σs(xy, ms) end[:,1]

# 物理的なものを選択

filter!(_data) do σs isphysical(σs, ms) end _data end ```
