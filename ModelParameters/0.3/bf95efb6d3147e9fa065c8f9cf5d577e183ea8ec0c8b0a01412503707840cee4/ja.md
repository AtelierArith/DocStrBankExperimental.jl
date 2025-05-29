```
mapflat(f, collection; maptype::Type=Union{NamedTuple,Tuple,AbstractArray})
```

`x`のすべてのネストされた非コレクション要素に`f`が適用される「フラット化された」バージョンの`map`です。変換された結果は、入力`x`のネストされた構造を変更せずに返されます。これは、通常`map`の後に`flatten`が続く関数的設定における`flatmap`とは異なることに注意してください。

# 例

```julia-repl
julia> mapflat(x -> 2*x, (a = (b = (1,)), c = (d = (2,))))
(a = (b = (2,)), c = (d = (4,)))
```
