```
フレシェコピュラ
```

フレシェコピュラ

フィールド:

  * n - マージナルの数
  * α - 最大コピュラのパラメータ
  * β - 最小コピュラのパラメータ

コンストラクタ

```
FrechetCopula(n::Int, α::Real)
```

1パラメータのフレシェコピュラは、最大コピュラの重みαと独立コピュラの重み1-αの組み合わせです。

コンストラクタ

```
FrechetCopula(n::Int, α::Real, β::Real)
```

2パラメータのフレシェコピュラ C = α C{max} + β C{min} + (1- α - β) C{⟂} は、n = 2 の場合のみサポートされています。

```jldoctest
julia> FrechetCopula(4, 0.5)
FrechetCopula(4, 0.5, 0.0)

julia> FrechetCopula(2, 0.5, 0.3)
FrechetCopula(2, 0.5, 0.3)
```
