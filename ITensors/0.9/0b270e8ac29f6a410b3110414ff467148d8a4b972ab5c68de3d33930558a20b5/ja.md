```
dense(T::ITensor)
```

新しいITensorを作成します。ストレージは最も近いDenseストレージになり、可能な限り新しいデータの割り当てを避けます。たとえば、Diagストレージを持つITensorは、対角値を除いてゼロで埋められたDenseストレージになります。
