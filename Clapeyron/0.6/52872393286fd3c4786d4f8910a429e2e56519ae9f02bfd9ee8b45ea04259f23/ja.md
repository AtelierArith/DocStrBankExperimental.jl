```
vdW1fRule <: vdW1fRuleModel

vdW1fRule(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

なし

## 説明

立方体パラメータのための van der Waals 一流体混合則：

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
ā = ∑aᵢⱼxᵢxⱼ√(αᵢ(T)αⱼ(T))
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
```

## モデル構築の例

```
# このモデルにはパラメータがないため、すべてのコンストラクタは同等です：
mixing = vdW1fRule()
mixing = vdW1fRule("水")
mixing = vdW1fRule(["水","二酸化炭素"])
```
