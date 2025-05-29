```
KayRule <: KayRuleModel

KayRule(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

なし

## 説明

立方体パラメータのためのKay混合則：

```
aᵢⱼ = √(aᵢaⱼ)(1 - kᵢⱼ)
bᵢⱼ = (1 - lᵢⱼ)(bᵢ + bⱼ)/2
ā = b̄*(∑[aᵢⱼxᵢxⱼ√(αᵢ(T)αⱼ(T))/bᵢⱼ])^2
b̄ = (∑∛(bᵢⱼ)xᵢxⱼ)^3
c̄ = ∑cᵢxᵢ
```

## モデル構築の例

```
# このモデルにはパラメータがないため、これらのコンストラクタはすべて同等です：
mixing = KayRule()
mixing = KayRule("水")
mixing = KayRule(["水","二酸化炭素"])
```
