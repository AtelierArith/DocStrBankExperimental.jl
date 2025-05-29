```
submap = get_submap(choices::ChoiceMap, addr)
```

addrで始まるすべての選択肢を含むサブアサインメントを返します。

指定されたアドレスに値が含まれている場合はエラーです。addrで始まるアドレスを持つ選択肢がない場合は、`EmptyChoiceMap`を返します。
