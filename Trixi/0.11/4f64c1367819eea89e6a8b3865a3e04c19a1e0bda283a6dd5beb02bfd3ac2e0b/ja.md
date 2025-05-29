```
FDSBP(D_SBP; surface_integral, volume_integral)
```

一般的な部分による総和（SBP）演算子を使用する[`DG`](@ref)メソッドの特殊化で、[SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl)から提供されています。特に、これは古典的な有限差分（FD）SBPメソッドを含みます。これらのメソッドは、古典的なDGメソッドと同じ構造を持ち、インターフェースを介しての接続を持つ要素上での局所操作を行い、連続性の制約を課しません。

`D_SBP`は、SummationByPartsOperators.jlからのSBP微分演算子です。他の引数は[`DG`](@ref)または[`DGSEM`](@ref)と同じ意味を持ちます。

!!! warning "実験的実装（アップウィンドSBP）"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

