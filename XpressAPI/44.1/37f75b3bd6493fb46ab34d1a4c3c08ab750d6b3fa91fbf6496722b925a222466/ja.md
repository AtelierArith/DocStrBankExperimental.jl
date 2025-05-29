```
XPRS_GLOBALBOUNDINGBOXAPPLIED
```

初期の解決が実行不可能であった後、GLOBALBOUNDINGBOX制御の絶対値に等しいバウンディングボックスが問題に適用されたかどうか、また適用された場合はどの変数に適用されたかを示します。（double）

値: 0 : バウンディングボックスは適用されていません（`XPRS_GLOBALBOUNDINGBOX_NOT_APPLIED`）。 1 : すべての元の変数にバウンディングボックスが適用されました（`XPRS_GLOBALBOUNDINGBOX_ORIGINAL`）。 2 : すべての元の変数と補助変数にバウンディングボックスが適用されました（`XPRS_GLOBALBOUNDINGBOX_AUXILIARY`）。
