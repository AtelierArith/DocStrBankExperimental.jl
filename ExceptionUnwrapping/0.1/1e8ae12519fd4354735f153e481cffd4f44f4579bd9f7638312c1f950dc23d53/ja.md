```
unwrap_exception(exception_wrapper) -> wrapped_exception
unwrap_exception(normal_exception) -> normal_exception

# カスタム例外タイプのオーバーライドを追加
ExceptionUnwrapping.unwrap_exception(e::MyWrappedException) = e.wrapped_exception
```

ラップされた例外を1レベル解除します。*新しいラップされた例外タイプは、この関数にメソッドを追加する必要があります。*

ラップされた例外の一例は、`TaskFailedException`で、これは`Task`によってスローされた例外を新しい`Exception`でラップし、タスクの失敗を説明します。

最初にどのような例外がスローされたかをテストするために例外を解除することは有用であり、異なるタイプの例外に対して異なる例外処理の動作が必要な場合に役立ちます。

新しいラップされた例外タイプの著者は、オーバーロードを追加することで、例外がラップしているフィールドを示すためにこれをオーバーロードできます。例えば：

```julia
ExceptionUnwrapping.unwrap_exception(e::MyWrappedException) = e.wrapped_exception
```

これはモジュール内の他の関数の実装で使用されます：

  * [`has_wrapped_exception(e, ::Type)`](@ref)
  * [`unwrap_exception_to_root(e)`](@ref)
