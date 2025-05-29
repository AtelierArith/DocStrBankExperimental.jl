```
DistributedObject{T}() where T
```

リモートプロセスに保存された型`<:T`のオブジェクトを参照する空の`DistributedObject`を作成します。

例えば、`DistributedObject{Int64}()`は、`Int64`オブジェクトを参照できる分散オブジェクトを返します。

```
DistributedObject{T}(f::Function; pids=workers()::Vector{Int64})
```

プロセス`pids`に保存された型`<:T`のオブジェクトへの参照を作成します。`f`は、`pids`の`pid`で実行されると、型`<:T`のオブジェクトの実装を返す必要がある関数です。デフォルトの`pids`はワーカープロセスです。

例えば、`DistributedObject((pid)->pid * ones(2); pids=[2,3])`は、ワーカー2および3にそれぞれ保存されたベクトル`[2,2]`および`[3,3]`を参照する分散オブジェクトを返します。

```
DistributedObject{T}(f::Function, pid::Int64)
```

プロセス`pid`に保存された型`<:T`のオブジェクトへの参照を作成します。`f`は、`pid`で実行されると、型`<:T`のオブジェクトの実装を返す必要がある関数です。

例えば、`DistributedObject(()->ones(2), 4)`は、ワーカー4に保存されたベクトル`[1,1]`を参照する分散オブジェクトを返します。
