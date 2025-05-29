```
System(crystal; <キーワード引数>)
```

SimpleCrystals.jlの`Crystal`構造体から`System`を構築します。

シミュレーションや分析で使用されないプロパティは、デフォルト値のままにしておくことができます。`atoms`、`atoms_data`、`coords`、および`boundary`は、`Crystal`構造体から自動的に計算されます。`σ`のような追加の原子パラメータは、便利なコンストラクタ`System(sys; <キーワード引数>)`を使用して、構築後に手動で追加する必要があります。
