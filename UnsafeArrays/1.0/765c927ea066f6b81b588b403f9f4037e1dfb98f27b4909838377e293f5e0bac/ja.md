```
uviews(f::Function, As::AbstractArray...)
```

`f(map(uview, As)...)` と同等です。実行中に `f` の配列 `As` をガーベジコレクションから自動的に保護します。

例:

```
uviews(A, B, ...) do (A_u, B_u, ...)
    # 安全でないビュー A_u, B_u, ... を使って何かをする
    # ここでのコードは A, B, ... をリサイズ/追加/etc. してはいけません
end
```

多くの場合、`views` の代わりに `@uviews` を使用する方が好ましいかもしれません。
