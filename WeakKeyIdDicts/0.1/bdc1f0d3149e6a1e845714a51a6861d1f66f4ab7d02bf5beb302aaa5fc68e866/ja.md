```
WeakKeyIdDict([itr])
```

`WeakKeyIdDict()` は、キーがオブジェクトへの弱い参照であるハッシュテーブルを構築します。これにより、ハッシュテーブル内で参照されていても、オブジェクトがガベージコレクションされる可能性があります。

さらなるヘルプについては、[`Dict`](https://docs.julialang.org/en/v1/base/collections/#Base.Dict) を参照してください。なお、[`Dict`](https://docs.julialang.org/en/v1/base/collections/#Base.Dict) とは異なり、`WeakKeyIdDict` は挿入時にキーを変換しません。これは、キーオブジェクトが挿入前にどこにも参照されていなかったことを意味します。

また、[`WeakRef`](https://docs.julialang.org/en/v1/base/base/#Core.WeakRef) や [`WeakKeyDict`](https://docs.julialang.org/en/v1/base/collections/#Base.WeakKeyDict) も参照してください。
