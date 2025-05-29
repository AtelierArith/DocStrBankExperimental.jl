```
NoTranslation(args...) <: TranslationModel
```

## 入力パラメータ

なし

## 説明

立方体モデルのデフォルトの体積翻訳モデルです。翻訳は行いません：

```
V = V₀ + mixing_rule(cᵢ)
cᵢ = 0 ∀ i
```

## モデル構築の例

```
# このモデルにはパラメータがないため、すべてのコンストラクタは同等です：
translation = NoTranslation()
translation = NoTranslation("water")
translation = NoTranslation(["water","carbon dioxide"])
```
