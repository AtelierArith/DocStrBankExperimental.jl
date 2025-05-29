```
get_combined_design(d::Design; diagnostics::Bool = false)
```

デザイン `d` のコピーを返します。ここで、パウリ X、Y、および Z 基準測定を説明する3つのパラメータが各キュービットの単一のパラメータに統合され、`diagnostics` が `true` の場合は診断情報が印刷されます。
