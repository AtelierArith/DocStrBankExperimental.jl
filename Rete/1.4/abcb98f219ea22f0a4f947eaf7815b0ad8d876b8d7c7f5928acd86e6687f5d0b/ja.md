```
add_forward_trigger(n::JoinNode, from::AbstractReteNode)
```

は、`from`をJoinNodeのフォワードトリガーとして追加します。

JoinNodeがそのフォワードトリガー入力の1つから事実を`receive`すると、その入力を他のすべての入力からの事実の組み合わせと結合し、`join_function`を実行します。それ以外の場合、JoinNodeはトリガーされません。
