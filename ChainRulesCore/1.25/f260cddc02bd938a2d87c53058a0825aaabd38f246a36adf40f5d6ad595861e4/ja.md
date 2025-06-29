```
NoTangent() <: AbstractZero
```

このタンジェントは、導関数が存在しないことを示しています。これは、整数やブール値（浮動小数点値を表すために使用されていない場合など）のような微分不可能な原始型のためのタンジェントタイプです。このような値を摂動させる唯一の有効な方法は、それらを全く変更しないことです。その結果、`NoTangent`は`ZeroTangent()`と機能的に同一ですが、追加の意味情報を提供します。

一般的に、原始に`NoTangent()`を追加することは間違いです：勾配ベースの手法は離散変数の最適化に使用できません。このようなケースをチェックしたい最適化パッケージがあるかもしれません。

!!! note
    これは導関数が実装されていないことを示すのではなく、数学的に定義されていないことを示しています。


これは主に次元、インデックス、またはサイズ引数に関する導関数として現れます。

```julia
function rrule(fill, x, len::Int)
    y = fill(x, len)
    fill_pullback(ȳ) = (NoTangent(), @thunk(sum(Ȳ)), NoTangent())
    return y, fill_pullback
end
```
