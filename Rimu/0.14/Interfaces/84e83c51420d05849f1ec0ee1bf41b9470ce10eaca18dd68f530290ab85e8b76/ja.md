```
sum_mutating!(accumulator, [f! = add!], iterator)
```

`iterator`の要素の合計を`accumulator`に加算し、結果を`accumulator`に格納します。`f!`が提供されている場合、それは2つの引数を受け取る必要があります。最初の引数は`accumulator`、2番目の引数は`iterator`の要素です。そうでない場合は、`add!`が使用されます。

関連情報は[`mapreduce`](@ref)を参照してください。
