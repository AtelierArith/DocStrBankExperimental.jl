```
ionstate(ion::Ion, sublevel)
```

`Ion`が状態$|sublevel⟩$にあることに対応するケートを返します。オプション: sublevel <: Tuple{String,Real}: フルサブレベル名を指定します sublevel <: String: サブレベルエイリアスを指定します sublevel <: Int: `sublevel`番目の固有状態を返します
