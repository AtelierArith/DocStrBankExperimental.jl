```
FV = extrude(shape::Matrix{<:AbstractFloat}, h; base=0.0, closed=true) -> GMTfv
```

2D/3D形状を押し出します。

### 引数

  * `shape`: 押し出す形状。Mx2またはMx3の行列または`GMTdataset`で定義された2Dポリゴンまたは3Dポリゴンである必要があります。
  * `h`: 押し出しの高さ。`shape`と同じ単位です。

### キーワード引数

  * `base`: 押し出す2D形状の基底高さ。デフォルトは0です。形状が3Dポリゴンの場合は無視されます。
  * `closed`: trueの場合（デフォルト）、上部と下部で形状を閉じます。

### 例

スイスを押し出す

```julia
	Dsw = coast(dump=true, DCW=(country=:CH, file=:ODS));	# スイスの国境を取得
	FV = extrude(Dsw, 0.2)
	viz(FV)
```
