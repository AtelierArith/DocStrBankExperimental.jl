```
unsubscribe(sf::ShadowFramework)
```

シャドウドキュメントのトピックからの購読を解除し、更新の処理を停止します。これを呼び出した後、`wait_until_synced(sf)`は再び`subscribe(sf)`を呼び出したことに対する最初の公開までブロックします。

各[`unsubscribe`](@ref)呼び出しが完了したときに完了するタスクを返します。また、各[`unsubscribe`](@ref)呼び出しからのパケットIDを含むコレクションも返します。
