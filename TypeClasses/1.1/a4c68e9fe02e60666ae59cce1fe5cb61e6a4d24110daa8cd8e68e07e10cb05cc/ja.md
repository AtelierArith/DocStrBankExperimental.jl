```
flatten(::A{A})::A = flatmap(identity, a)
```

`flatten` は1つのネストのレベルを取り除きます。デフォルトのフォールバックとして `flatmap` を使用します。
