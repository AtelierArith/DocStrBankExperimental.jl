1次元の線形補間

##### フィールド

  * `breaks::AbstractVector` : 補間を行うためのソートされたグリッドポイントの配列
  * `vals::AbstractVector` : 各グリッドポイントに関連付けられた関数値

##### 例

```julia
breaks = cumsum(0.1 .* rand(20))
vals = 0.1 .* sin.(breaks)
li = LinInterp(breaks, vals)

# LinInterpオブジェクトの`call`メソッドを介して補間を行う
li(0.2)

# ブロードキャスティングを使用して複数のポイントで評価する
li.([0.1, 0.2, 0.3])
```
