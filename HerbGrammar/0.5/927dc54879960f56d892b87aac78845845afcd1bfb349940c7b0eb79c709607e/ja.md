```
isterminal(rule::Any, types::AbstractVector{Symbol})
```

ルールが終端である場合、すなわち提供されたベクター内のいずれかのタイプを含まない場合にtrueを返します。例えば、:(x)は終端であり、:(1+1)も終端ですが、:(Real + Real)は通常はそうではありません。
