```
Bodies(bodies, ops::AbstractVector)
```

  * `bodies::Vector{AutoBody}`: `AutoBody`のベクター
  * `ops::Vector{Function}`: 複数の`AutoBody`の重ね合わせのための演算子のベクター

複数の`body::AutoBody`オブジェクトを演算子`ops`に従って重ね合わせます。これは`AutoBody`に実装された演算子によって手動で行うこともできますが、あまりにも多くのボディを追加すると、`sdf`および`map`関数の再帰問題がスタックに収まらなくなる可能性があります。このタイプは、再帰ではなく反復によってボディの重ね合わせを実装し、`sdf`および`map`関数の削減は`mesure`関数で行われ、事前には行われません。演算子ベクター`ops`は、`bodies`ベクター内の2つの連続する`AutoBody`間で呼び出す操作を指定します。`Bodies`間でサポートされている唯一の操作は`+`（またはエイリアス`∪`）であることに注意してください。
