```
freeze(@nospecialize(ids::T)) where {T<:Union{IDS,IDSvector}}
```

新しいIDSを返し、すべての式が評価されます（データはコピーされます）

注意：失敗した式は`missing`になります
