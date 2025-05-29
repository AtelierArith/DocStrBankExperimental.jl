```
LinearMixing <: MultiFluidDepartureModel
LinearMixing(components;
userlocations = String[],
verbose = false)
```

## 入力パラメータ

なし

## 説明

多パラメータEoSモデルのための線形混合ルール：

```
τ = T̄/T
δ = V̄/V
V̄ = ∑xᵢVcⱼ
T̄ = ∑xᵢTcᵢ
```

## モデル構築の例

```
# このモデルにはパラメータがないため、これらのコンストラクタはすべて同等です：
mixing = LinearMixing()
mixing = LinearMixing("水")
mixing = LinearMixing(["水","二酸化炭素"])
```
