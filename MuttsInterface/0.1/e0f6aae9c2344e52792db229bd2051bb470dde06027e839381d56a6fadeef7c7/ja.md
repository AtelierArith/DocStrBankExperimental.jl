```
is_mutts_type(t::Type) -> Bool
```

型 `t` が `@mutt` マクロを介して作成された場合に true を返します。これは、Mutable Til Shared 型であり、*mutable-until-shared* 規則を実装しています。これらの型は最初は可変であり、`mark_immutable!` および `branch!` を介して凍結されたバージョンに保存できます。
