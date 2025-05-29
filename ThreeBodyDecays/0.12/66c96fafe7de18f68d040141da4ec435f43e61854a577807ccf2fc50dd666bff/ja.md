`ThreeBodyDecay`(; chains, couplings, names)

指定されたパラメータを持つ `ThreeBodyDecay` オブジェクトを構築します。

# 引数

  * `chains`: 崩壊に関与するチェーンの配列。この配列の長さは `couplings` と `names` の長さと一致する必要があります。
  * `couplings`: 崩壊の各チェーンに対する結合定数の配列。この配列の長さは `chains` と `names` の長さと一致する必要があります。
  * `names`: 各チェーンの名前、または崩壊における共鳴の名前の配列。この配列の長さは `chains` と `couplings` の長さと一致する必要があります。

# 戻り値

  * 指定されたチェーン、結合定数、および名前を持つ `ThreeBodyDecay` オブジェクト。

# 例

```julia
ThreeBodyDecay(
chains=[chain1, chain2, chain3],
couplings=[1.0, -1.0, 0.2im],
names=["L1405", "L1405", "K892"])
```
