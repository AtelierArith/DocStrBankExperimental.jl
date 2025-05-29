```
array(T::ITensor)
```

ITensor `T`を与えると、ITensorの要素のコピーを持つArrayを返すか、ITensorのストレージがDenseの場合はビューを返します。

Array内の要素の順序は、どのIndexが行として扱われ、どのIndexが列として扱われるかに依存し、ITensorの内部レイアウトによります。

!!! warning
    このメソッドは開発者専用であり、ITensorアプリケーションでの使用は推奨されません。自分が何をしているのか（例えば、インデックスを特定の順序に置換したためにITensorのメモリ順序が確実である場合）を理解している場合を除きます。


関連情報としては [`matrix`](@ref)、[`vector`](@ref) があります。
