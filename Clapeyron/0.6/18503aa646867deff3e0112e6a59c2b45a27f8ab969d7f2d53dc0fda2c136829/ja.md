```
ClausiusAlpha <: ClausiusAlphaModel

ClausiusAlpha(components;
userlocations = String[],
verbose::Bool=false)
```

## 入力パラメータ

  * なし

## 説明

立方体アルファ `(α(T))` モデル。デフォルトは [`Clausius`](@ref) と [`Berthelot`] 

```
αᵢ = 1/Trᵢ
Trᵢ = T/Tcᵢ
```

## モデル構築の例

```
# このモデルにはパラメータがないため、すべてのコンストラクタは同等です：
alpha = ClausiusAlpha()
alpha = ClausiusAlpha("水")
alpha = ClausiusAlpha(["水","二酸化炭素"])
```
