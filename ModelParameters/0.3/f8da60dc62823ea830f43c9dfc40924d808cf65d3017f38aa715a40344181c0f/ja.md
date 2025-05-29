```
update!(m::MutableModel, table)
```

Tables.jlインターフェースを実装したオブジェクトからモデルをインプレースで更新します。

注意: 親オブジェクトは不変であっても、完全に再構築されます。しかし、ラッパー`AbstractModel`は可変であり、`Model`や`InteractModel`のようになります。
