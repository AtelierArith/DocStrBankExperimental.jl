```
KeyedDataset
```

`KeyedDataset`は、共有次元に制約のあるコンポーネント`KeyedArray`の関連コレクションを説明します。

# フィールド

  * `constraints::OrderedSet{Pattern}` - 共有次元に関する制約[`Pattern`](@ref)。
  * `data::LittleDict{Tuple, KeyedArray}` - タプルコンポーネントキー配列としてフラット化されたキー経路。
