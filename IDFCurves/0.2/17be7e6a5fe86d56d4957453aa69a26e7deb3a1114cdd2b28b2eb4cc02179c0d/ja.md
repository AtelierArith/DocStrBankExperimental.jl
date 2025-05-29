```
qqplotci(fm::MarginalScalingModel, α::Real=.05, H::PDMat{<:Real})
```

分位数-分位数プロットと信頼区間/信用区間のレベル `1-α`。

## 詳細

この関数は、引数で提供されたヘッセ行列 `H` を使用します。  
