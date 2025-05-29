```
getallvalues(v::AbstractThreadLocal{T})::AbstractVector{T}
```

スレッドローカル値のすべての値（各スレッドごとに1つ）にベクトルとしてアクセスします。シングルスレッドのコードセクションでのみ呼び出すことができます。
