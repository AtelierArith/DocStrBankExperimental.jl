```
array(T::ITensor, inds...)
```

ITensor `T`をArrayに変換します。

Array内の要素の順序は、入力インデックス`inds`によって指定されます。これは、ITensorのストレージがDenseであり、インデックスがすでに指定された順序になっている場合、可能な限りコピーを避けるようにします（つまり、元のデータのビューを返すことがあります）。

!!! warning
    将来的には、特定のストレージタイプに対して特化したAbstractArrayタイプを返す可能性があることに注意してください。たとえば、`Diag`ストレージを持つITensorに対して`LinearAlgebra.Diagonal`タイプを返すことがあります。特定のストレージタイプに依存しないでください。


関連情報としては、[`matrix`](@ref)、[`vector`](@ref)があります。
