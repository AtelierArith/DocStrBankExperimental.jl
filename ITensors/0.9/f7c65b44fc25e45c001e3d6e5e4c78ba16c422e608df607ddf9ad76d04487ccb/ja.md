```
vector(T::ITensor, inds...)
```

ITensor `T`をVectorに変換します。

Array内の要素の順序は、入力インデックス`inds`によって指定されます。これは、ITensorのストレージがDenseであり、インデックスがすでに指定された順序になっている場合、コピーを避けることを試みます（つまり、元のデータのビューを返す可能性があります）。

!!! warning
    将来的には、特定のストレージタイプに対して特化したAbstractArrayタイプを返す可能性があることに注意してください。例えば、`Diag`ストレージを持つITensorに対して`LinearAlgebra.Diagonal`タイプを返すことがあります。特定のストレージタイプに依存しないでください。


他にも[`array`](@ref)、[`matrix`](@ref)を参照してください。
