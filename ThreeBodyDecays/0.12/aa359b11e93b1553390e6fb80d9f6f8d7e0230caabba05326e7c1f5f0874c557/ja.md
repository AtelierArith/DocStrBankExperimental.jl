ThreeBodyDecay(descriptor)

`ThreeBodyDecay`オブジェクトを1つの引数、descriptorを使用して構築します。`descriptor`は、`names .=> zip(couplings, chains)`のペアのリストです。

# 例

```julia
ThreeBodyDecay("K892" .=> zip([1.0, -1.0, 0.2im], [chain1, chain2, chain3]))
```
