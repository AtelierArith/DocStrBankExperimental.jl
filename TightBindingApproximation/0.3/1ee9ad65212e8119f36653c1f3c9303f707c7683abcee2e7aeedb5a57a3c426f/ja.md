```
infinitesimal(::TBAKind{:TBA}) -> 0
infinitesimal(::TBAKind{:BdG}) -> atol/5
infinitesimal(::Fermionic{:BdG}) -> 0
```

マトリクス化において使用される無限小は、ゴールドストーンモードを捉えるためのタイトバインディング近似において使用されます。
