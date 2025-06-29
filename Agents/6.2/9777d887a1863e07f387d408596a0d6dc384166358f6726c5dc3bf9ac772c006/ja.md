```
random_agent(model, condition; optimistic=true, alloc = false) → agent
```

条件 `condition(agent) == true` を満たすモデルからランダムなエージェントを返します。この関数はエージェントIDのランダムな順列を生成し、それを反復処理します。条件を満たすエージェントがいない場合は、代わりに `nothing` が返されます。

## キーワード

`optimistic = true` は、使用されるアルゴリズムを非割り当てに変更しますが、パフォーマンスの変動が大きくなる可能性があります。条件が人口の大部分に対して `true` である場合（たとえば、エージェントがグループに分けられている場合）、これにより速度が向上するはずです。

`alloc` は、楽観的なバージョンが条件を満たすエージェントを見つけられなかった場合に、異なるフォールバック戦略を使用するために使用できます。フィルタリング条件が高コストである場合、割り当てを行うフォールバックの方がパフォーマンスが向上する可能性があります。
