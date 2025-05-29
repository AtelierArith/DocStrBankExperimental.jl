```
ErrorResult(::Type{T}, exception::E) -> Result{T, E}
ErrorResult(::Type{T}, exception::AbstractString="") -> Result{T, ErrorException}
```

型 `T` の値または型 `E` の例外を保持できる `Result` を作成し、そこに `exception` を格納します。`exception` がテキストとして提供される場合、それは一般的な `ErrorException` にラップされます。例外が提供されない場合は、空の文字列を持つ `ErrorException` が使用されます。型引数が提供されない場合は、`Any` が使用されます。

`ErrorResult` は `Result` を作成するための便利な関数であり、独自の型ではありません。
