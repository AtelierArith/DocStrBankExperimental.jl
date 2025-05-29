```
@constant x = value
```

プライベートメソッド（テストで使用）。

`const x = value` と同等ですが、次のようにバインディングを登録します：

```julia
MLJBase.HANDLE_GIVEN_ID[objectid(value)] = :x
```

登録されたオブジェクトは、`show(x)` などの呼び出しでバインドされた変数名を使用して表示されます。

!!! warning
    すべての `const` 宣言と同様に、同じ型の新しい値に `x` をバインドすることは防止されず、登録は更新されません。

