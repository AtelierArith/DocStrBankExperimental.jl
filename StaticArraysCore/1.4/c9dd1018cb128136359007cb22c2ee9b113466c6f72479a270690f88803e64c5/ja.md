```
similar_type(static_array)
similar_type(static_array, T)
similar_type(array, ::Size)
similar_type(array, T, ::Size)
```

入力配列（または型）`static_array`/`array`に類似した静的サイズの配列のコンストラクタを返します。オプションで異なる要素型`T`やサイズ`Size`を指定できます。入力`array`が`StaticArray`でない場合、`Size`は必須です。

これは`similar()`とは異なり、結果として得られる配列型は変更不可能である可能性があり（または`setindex!()`を定義しない可能性があり）、したがって返される型はそのデータで*構築*される必要があるかもしれません。

（オプションの）サイズは*必ず*静的な`Size`オブジェクトとして指定する必要があります（コンパイラが結果を静的に推論できるようにするため）。

新しい型は、デフォルトの動作をオーバーロードしたい場合、`similar_type(::Type{A},::Type{T},::Size{S}) where {A<:MyType,T,S}`というシグネチャを定義する必要があります。
