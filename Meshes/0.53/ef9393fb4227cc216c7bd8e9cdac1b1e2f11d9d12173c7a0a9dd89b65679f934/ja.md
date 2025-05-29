```
Ngon(p₁, p₂, ..., pₙ)
```

N-gonは、`N ≥ 3`の頂点`p₁`、`p₂`、...、`pₙ`を持ち、反時計回り（CCW）に配置された多角形です。この場合、頂点の数は固定されており、コンパイル時に既知です。N-gonの例には、`Triangle`（N=3）、`Quadrangle`（N=4）、`Pentagon`（N=5）などがあります。

### 注意事項

頂点の数`N`はコンパイル時に既知ですが、抽象ベクトルを使用して頂点のリストを格納します。この設計により、高価なメモリ割り当てなしでグローバルベクトルのビューからN-gonを構築することができます。

型エイリアスは`Triangle`、`Quadrangle`、`Pentagon`、`Hexagon`、`Heptagon`、`Octagon`、`Nonagon`、`Decagon`です。
