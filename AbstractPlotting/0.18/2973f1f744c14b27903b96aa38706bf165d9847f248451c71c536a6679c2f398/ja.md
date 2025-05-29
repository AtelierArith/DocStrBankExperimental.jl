```
map_once(closure, inputs::Node....)::Node
```

Reactive.foreachのように、参照が保持されていなくても保存されます。違いは、同じクロージャでmap onceを複数回呼び出すことができ、古い結果のNodeを閉じて新しいものを登録することです。

```function test(s1::Node)     s3 = map*once(x-> (println("1 ", x); x), s1)     s3 = map*once(x-> (println("2 ", x); x), s1)

end test(Node(1), Node(2))

>
```
