```
imap(f, xs1, [xs2, ...])
```

1つ以上のイテレータからの連続する値に適用された関数の値を反復処理します。`Iterators.zip`のように、入力イテレータのいずれかが尽きたときにイテレータは終了します。

```jldoctest
julia> for i in imap(+, [1,2,3], [4,5,6])
            @show i
       end
i = 5
i = 7
i = 9
```
