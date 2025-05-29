```
has_wrapped_exception(e, ExceptionType)::Bool
```

与えられた例外インスタンス `e` が、そのアンラップされた例外のチェーンのどこかにタイプ `T` の例外を含む場合、true を返します。

アプリケーションコードは、ライブラリがユーザーの例外をラップする際にコードが壊れないように、catch ブロック内で `e isa T` の代わりに `has_wrapped_exception(e, T)` を使用することを推奨します。

これにより、アプリケーションコードは、ラップされた例外を引き起こす可能性のあるライブラリの変更（例えば、基盤となる並行性の決定に対する変更など）に対して耐性を持つことができます（したがって、並行性の協調的な利点を維持します）。

# 例

```julia
try
    # もしこれが将来的に並行処理になる場合、catch ブロックは変更する必要がありません。
    library_function(args...)
catch e
    if has_wrapped_exception(e, MyExceptionType)
        unwrapped = unwrap_exception_until(e, MyExceptionType)
        handle_my_exception(unwrapped, caught=e)
    else
        rethrow()
    end
end
```
