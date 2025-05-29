```
struct SUWeight{E<:PEPSWeight}
```

シュミットボンド重みは、シンプル/クラスタ更新で使用されます。重みの要素は常に実数です。

## フィールド

  * `data::Array{E, 3} where E<:(TensorKit.AbstractTensorMap{T, S, 1, 1} where {T, S})`

## コンストラクタ

```
SUWeight(wts_mats::AbstractMatrix{E}...) where {E<:PEPSWeight}
```
