```
function agent_actions(m::JointMDP, idx::Int64, s::S) where S
```

指定されたエージェントインデックスの離散アクションを返します。

!!! note
    これは非常に多く呼び出されるため、毎回アロケートしないようにするべきです....

