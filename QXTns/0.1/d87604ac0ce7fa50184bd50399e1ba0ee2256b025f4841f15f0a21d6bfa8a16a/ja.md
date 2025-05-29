```
contract_pair!(tn::TensorNetwork, A_id::Symbol, B_id::Symbol; mock::Bool=false)
```

'tn'内のテンソルを'A*id'と'B*id'のIDで収束させます。mockフラグがtrueの場合、新しいテンソルは正しい次元を持つモックテンソルになりますが、実際のデータは含まれません。

結果のテンソルは、提供された場合はシンボル`C_id`の下に`tn`に保存されます。そうでない場合は、新しいIDが作成されます。
