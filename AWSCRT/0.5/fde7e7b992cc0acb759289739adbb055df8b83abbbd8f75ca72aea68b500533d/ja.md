```
wait_until_synced(f::Function, sf::ShadowFramework)
```

ブローカーとシャドウドキュメントが同期されるまでブロックします。あなたが行う公開の後に同期を待ちたい場合は、その公開をラムダ `f` の中で行う必要があります。
