```
ContextManager(func)
```

ContextManagerは、前処理と場合によってはクリーンアップステップを持つ計算を示します。

単一の引数は、継続関数を1つの引数として受け取る関数である必要があります。以下のように考えてください：

```julia
function contextmanagerready(cont)
  # ... 前に何かをする
  value = ... # 後で作業するための値を作成
  result = cont(value)  # 値を継続関数に渡す（`yield`のように考えてください）
  # ... 終了前に何かをする、例えばクリーンアップ
  result # 重要：常に`cont`関数の結果を返す
end
```

これを`ContextManager(contextmanagerready)`でラップすることができ、すぐにすべてのコンテキストマネージャ機能を使用できます。

括弧を少なくするためのシンプルな`@ContextManager`があります。

```julia
mycontextmanager(value) = @ContextManager function(cont)
  println("got value = $value")
  result = cont(value)
  println("finished value = $value")
  result
end
```

---

これを2つの方法で実行できます。継続関数として`Base.identity`を渡すだけです。

```julia
julia> mycontextmanager(4)(x -> x)
got value = 4
finished value = 4
```

また、便利のために`Base.run`もオーバーロードしています。

```julia
# 追加の引数なしで、Base.identityでコンテキストマネージャを実行
run(mycontextmanager(4))
# 指定された継続関数でも動作し、素敵なdo構文になります
run(x -> x, mycontextmanager(4))
run(mycontextmanager(4)) do x
  x
end
```
