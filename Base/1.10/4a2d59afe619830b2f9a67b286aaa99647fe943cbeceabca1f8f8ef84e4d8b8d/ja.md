```
mapfoldr(f, op, itr; [init])
```

[`mapreduce`](@ref)と同様ですが、[`foldr`](@ref)のように右結合性が保証されています。指定された場合、キーワード引数`init`は正確に1回使用されます。一般的に、空のコレクションで作業するには`init`を提供する必要があります。
