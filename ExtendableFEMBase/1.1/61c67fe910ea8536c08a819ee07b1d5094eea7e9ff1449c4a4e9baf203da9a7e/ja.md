```
function nodevalues_view(
	source::FEVectorBlock,
	operator::Type{<:AbstractFunctionOperator} = Identity)
```

ソースブロックのノード値のビューのベクトルを返します（現在、非破壊H1準拠要素に対して機能します）で、係数に直接アクセスします。
