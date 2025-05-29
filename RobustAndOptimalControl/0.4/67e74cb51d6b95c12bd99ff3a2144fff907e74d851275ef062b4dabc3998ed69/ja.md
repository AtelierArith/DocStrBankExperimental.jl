```
extended_controller(K::AbstractStateSpace)
```

コントローラーを受け取り、拡張入力 `[r; y]` と出力 `y` を持つ `ExtendedStateSpace` バージョンを返します（`z` 出力は0次元です）。
