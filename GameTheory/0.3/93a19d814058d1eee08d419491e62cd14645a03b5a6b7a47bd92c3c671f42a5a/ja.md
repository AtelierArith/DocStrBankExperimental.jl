```
NormalFormGame(players...)
```

N人プレイヤーのNormalFormGameのコンストラクタで、N人のPlayerインスタンスを持ちます。

# 引数

  * `players::Player{N,T}...` : N人のPlayerインスタンス

# 例

```julia
# p1, p2, および p3 はすべて `Player{3,T}` 型で、ある `T` に対して
NormalFormGame(p1, p2, p3)
```
