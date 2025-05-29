```
returnlevelplotci(fm::AbstractFittedExtremeValueModel, α::Real=.05)
```

リターンレベルプロットとレベル `1-α` の信頼区間/信用区間を返します。

## 注意

この関数は現在、定常モデルにのみ利用可能です。

[`returnlevelplotci`](@ref) および [`qqplot`](@ref) も参照してください。   

## 例

```@example
using Distributions, Extremes

pd = GeneralizedExtremeValue(0,1,0)
y = rand(pd, 300)
fm = gevfit(y)

returnlevelplotci(fm)
```
