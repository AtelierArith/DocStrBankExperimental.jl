```
MidpointDisplacement <: NeutralLandscapeMaker

MidpointDisplacement(; H = 0.5)
```

ミッドポイントディスプレイスメントアルゴリズムオブジェクト `MidpointDisplacement` を作成します。空間的自己相関の度合いは、0.0（低自己相関）から1.0（高自己相関）まで変化するパラメータ `H` によって制御されます - これは非包括的であり、H = 0 および H = 1 は期待通りに動作しません。

類似のアルゴリズムであるダイヤモンド-スクエアは、ほぼ同様に機能しますが、ダイヤモンド-スクエアでは、スクエアステップが最も近い2つのコーナーとスクエアの中心からエッジのミッドポイントを補間するのに対し、`MidpointDisplacement` は最も近いコーナーからのみ補間します（`DiamondSquare` を参照）。
