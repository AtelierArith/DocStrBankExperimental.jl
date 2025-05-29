```
BridgeElement(elementStart::Element, posStart::Float64, elementEnd::Element, posEnd::Float64, section::Section, id = :element; release = :fixedfixed)
```

2つのフレーム要素の間に橋要素を作成します。`elementStart`から`elementStart.nodeStart.position`から`elementStart.length * posStart`の位置に接続し、`elementEnd`から`elementEnd.nodeStart.position`から`elementEnd.length * posEnd`の位置に接続します。すなわち、`posStart, posEnd ∈ ]0, 1[`
