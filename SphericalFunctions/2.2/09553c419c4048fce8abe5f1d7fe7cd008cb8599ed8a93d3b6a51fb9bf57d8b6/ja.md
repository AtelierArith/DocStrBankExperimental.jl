```
Yrange(ℓₘᵢₙ, ℓₘₐₓ)
```

(ℓ, m) インデックスの配列を Y 配列のように作成します

## パラメータ

ℓₘᵢₙ : int     0 <= ℓₘᵢₙ <= ℓₘₐₓ を満たす整数 ℓₘₐₓ : int     0 <= ℓₘᵢₙ <= ℓₘₐₓ を満たす整数

## 戻り値

i : int     下記のように配置されたモード重みの配列の合計サイズ

## 参照

Ysize : モード重みの配列の合計サイズ Yindex : モード重み配列の特定の要素のインデックス

## 注意事項

これは、モードが (固定された s 値で) 次のように配置されていると仮定します

```
[
    Y(s, ℓ, m)
    for ℓ ∈ ℓₘᵢₙ:ℓₘₐₓ
    for m ∈ -ℓ:ℓ
]
```
