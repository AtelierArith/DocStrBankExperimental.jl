```
balance!(A; scale=true, permute=true) => Abal, B::Balancer
```

正方行列をバランスさせて、さまざまな操作がより安定するようにします。

`permute`が真の場合、行と列の置換が見つかり、`Abal`はブロック形式`[T₁ X Y; 0 C Z; 0 0 T₂]`を持ち、ここで`T₁`と`T₂`は上三角行列です。`scale`が真の場合、2の累乗を使用した対角類似変換が見つかり、`C`ブロックの1ノルム（または置換しない場合は`Abal`全体）がほぼ1に近くなります。変換は`B`にエンコードされ、固有ベクトルなどのために逆変換できるようになります。バランスを取ることで、固有解析の精度が通常向上します。
