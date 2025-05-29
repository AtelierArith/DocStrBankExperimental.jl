```
UnitSystems.similitude() = haskey(ENV,"SIMILITUDE")
```

オプションの環境変数 `ENV["SIMILITUDE"]` により、`UnitSystems.similitude()` は `true` を返すようになり、`UnitSystems`（デフォルト）と `Similitude`（環境変数の指定が必要）との間で使用を切り替える際に依存関係を構築する柔軟性が得られます。例えば、`MeasureSystems` と `Geophysics` では、このオプションを使用してローカルコンパイルワークフローの多様性に対する柔軟性を高めています。
