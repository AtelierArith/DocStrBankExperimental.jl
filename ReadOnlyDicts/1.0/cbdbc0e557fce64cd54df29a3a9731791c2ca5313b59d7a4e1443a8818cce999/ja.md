```julia
struct ReadOnlyDict{K, V, D<:AbstractDict{K, V}} <: AbstractDict{K, V}
```

`AbstractDict`をラップし、インターフェースの非変更関数のみを実装します。ラップされた`AbstractDict`は`Base.parent`を使用して取得できます。標準の辞書コンストラクタは、内部コレクションとして`Base.Dict`を使用します。
