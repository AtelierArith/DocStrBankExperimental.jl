```
zip_longest(iters...; default=nothing)
```

1つ以上の反復可能オブジェクトに対して、各入力反復可能オブジェクトの`i`番目のコンポーネントが終了していない場合はそのコンポーネントを、そうでない場合は`default`を含むタプルの反復可能なオブジェクトを返します。`default`はスカラーでも、反復可能オブジェクトごとに1つのデフォルトを持つタプルでも構いません。

```jldoctest
julia> for t in zip_longest(1:2, 5:8)
         @show t
       end
t = (1, 5)
t = (2, 6)
t = (nothing, 7)
t = (nothing, 8)

julia> for t in zip_longest('a':'e', ['m', 'n']; default='x')
         @show t
       end
t = ('a', 'm')
t = ('b', 'n')
t = ('c', 'x')
t = ('d', 'x')
t = ('e', 'x')
```
