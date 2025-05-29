```
Legolas.SchemaVersion{name,version}
```

Legolasスキーマの特定のバージョンを表す型です。関連する`name`（`Symbol`型）と`version`（`Integer`型）は型パラメータとして表面化され、ディスパッチに利用できるようになっています。

詳細と例については、`Legolas.jl/examples/tour.jl`およびLegolas.jlドキュメントの「スキーマ関連の概念/規約」セクションを参照してください。

コンストラクタ`SchemaVersion{name,version}()`は、`version`が負の場合に`ArgumentError`をスローします。

関連情報: [`Legolas.@schema`](@ref)
