```
uview(A::AbstractArray, I...)
```

`view`の非安全な同等物。`I...`と`A`の型に応じて、`UnsafeArray`、標準の`SubArray`、または`A`自体を返す場合があります。

`uview`が`UnsafeArray`を返す可能性があるため、`A`自体とその内容は、ビューが使用されている間、ガーベジコレクションから*必ず*保護される必要があります（例：Julia > v0.6の`GC.@preserve`を使用）。

自動的にGC保護を行いながら、1つまたは複数の配列の非安全なビューを使用するには、`uviews(f::Function, As::AbstractArray...)`または`@uviews A ... expr`を使用します。

```
uviews(A, B, ...) do (A_u, B_u, ...)
    # 非安全なビューA_u, B_u, ...を使って何かを行う
    # ここでのコードはA, B, ...をリサイズ/追加/etc.してはいけません
end
```

カスタム配列型の`uview`をサポートするには、関数`UnsafeArrays.unsafe_uview`にメソッドを追加します。
