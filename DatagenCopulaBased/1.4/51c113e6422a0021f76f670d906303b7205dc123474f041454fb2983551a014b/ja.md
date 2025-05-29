```
ChainFrechetCopulas
```

バイバリアントフレシェコピュラのチェーン。各後続のマージナルペアをバイバリアントフレシェコピュラによってモデル化します。

フィールド:     - n::Int - マージナルの数     - α::Vector{Real}  - 最大コピュラのためのパラメータのベクトル     - β::Vector{Real} - 最小コピュラのためのパラメータのベクトル

ここで、α[i]とβ[i]はi番目とi+1番目のマージナル間のバイバリアントフレシェコピュラをパラメータ化します。

コンストラクタ

```
ChainFrechetCopulas(α::Vector{Real})
```

ここでβ = zero(0)

```
ChainFrechetCopulas(α::Vector{Real}, β::Vector{Real})
```

```jldoctest
julia> ChainFrechetCopulas([0.2, 0.3, 0.4])
ChainFrechetCopulas(4, [0.2, 0.3, 0.4], [0.0, 0.0, 0.0])

julia> ChainFrechetCopulas([0.2, 0.3, 0.4], [0.1, 0.1, 0.1])
ChainFrechetCopulas(4, [0.2, 0.3, 0.4], [0.1, 0.1, 0.1])
```
