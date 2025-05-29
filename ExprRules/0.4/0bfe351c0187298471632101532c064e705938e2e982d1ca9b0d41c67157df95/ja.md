```
isterminal(rule::Any, types::AbstractVector{Symbol})
```

ルールが終端である場合、つまり提供されたベクター内のタイプを含まない場合にtrueを返します。例えば、:(x)は終端であり、:(1+1)は終端ですが、:(Real + Real)は通常はそうではありません。
