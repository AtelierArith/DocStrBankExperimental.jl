```
denseblocks(T::ITensor)
```

スパース形式（対角スパースなど）を持つブロックをすべて密にしながら、外部のブロックスパース構造を保持する新しいITensorを作成します。このメソッドは、可能な限り新しいデータの割り当てを避けます。

例えば、DiagBlockSparseストレージを持つITensorは、その後BlockSparseストレージを持つことになります。
