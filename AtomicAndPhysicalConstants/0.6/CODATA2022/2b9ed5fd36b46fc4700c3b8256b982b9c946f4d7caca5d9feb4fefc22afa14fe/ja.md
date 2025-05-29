```
showconst(
    query::Symbol = :constants
)
```

## 説明:

パッケージ内の利用可能な定数をリストします

## パラメータ:

  * `query`     – 型:`Symbol`、知りたい定数のタイプ

## オプション:

  * `:constants`      – すべての物理定数をリスト
  * `:subatomic`      – すべての可能な亜原子粒子をリスト
  * `:(atomic symbol)`– その原子種のすべての同位体をリスト、例: :Fe
