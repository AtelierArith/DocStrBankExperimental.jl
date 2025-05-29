```
connection_matrix(lc::LefschetzComplex, mvf::CellSubsets;
                  [returnbasis::Bool])
```

Lefschetz複体`lc`上の多重ベクトル場`mvf`の接続行列を計算します。この行列は、Lefschetz複体の境界行列に関連する体上で定義されます。

この関数は、`ConleyMorseCM`型のオブジェクトを返します。オプションの引数`returnbasis::Bool=true`が指定されている場合、関数は接続行列の列の基底を元のラベルに基づいて示す辞書も返します。
