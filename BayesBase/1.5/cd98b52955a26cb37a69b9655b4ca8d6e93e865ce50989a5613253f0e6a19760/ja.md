```
LinearizedProductOf
```

複数の分布の積の効率的な**線形化**実装です。この構造は、同一のオブジェクトがある場合に`ProductOf`ツリーが過度に成長するのを防ぎます。このトリックは、閉じた積のルールが利用できない場合でも、分布が同じタイプであるときにJuliaのコンパイル時間を大幅に短縮します。本質的に、この構造は、同じタイプのオブジェクトを見た場合に`ProductOf`ツリーの葉を線形化します（ディスパッチを介して）。

参照: [`ProductOf`](@ref), [`GenericProd`]
