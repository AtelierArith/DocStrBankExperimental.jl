```
NLLSsolver.nres(mycost)
```

`mycost` が生成する残差の数を返します。返り値は整数でなければならず、できれば静的で、最適化中に変わってはいけません。

# 例

残差ブロックタイプ `MyResidual <: AbstractResidual` がその `computeresidual` メソッドから長さ3の残差ベクトルを返す場合、

```julia
    NLLSsolver.nres(::MyCost) = static(3)
```

!!! tip
    残差の長さがコンパイル時に知られている場合は、静的整数を返してください。


!!! note
    必要なユーザー特化API関数です。

