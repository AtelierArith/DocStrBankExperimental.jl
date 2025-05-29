```
RunIf(f, rule)
```

`RunIf`は、`SimData`オブジェクトとセルの状態およびインデックスを渡して、ルールを条件でラップすることを可能にします。

`$julia RunIf(dispersal) do data, state, I     state >= oneunit(state) end$`
