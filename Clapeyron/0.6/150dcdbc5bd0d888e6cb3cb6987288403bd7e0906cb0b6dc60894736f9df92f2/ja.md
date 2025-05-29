```
NoAlpha(args...) <: NoAlphaModel
```

## 入力パラメータ

なし

## 説明

立方体アルファ `(α(T))` モデル。デフォルトは [`vdW`](@ref) EoS

```
αᵢ = 1 ∀ i
```

## モデル構築の例

```
# このモデルにはパラメータがないため、これらのコンストラクタはすべて同等です：
alpha = NoAlpha()
alpha = NoAlpha("水")
alpha = NoAlpha(["水","二酸化炭素"])
```
