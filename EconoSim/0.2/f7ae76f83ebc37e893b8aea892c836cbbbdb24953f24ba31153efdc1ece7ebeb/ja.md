```
process_needs(needs::Needs
            type::NeedType,
            posessions::Entities = Entities())
```

指定されたニーズタイプのアクターのすべてのニーズのベクターを取得します。ベクターには、名前付きタプル {blueprint::Blueprint, units::Int} が含まれています。ニーズタイプが優先されている場合、リストは優先度の順に並べられ、それ以外の場合はランダム化されます。
