```
TimeSteppingStrategy(dict::Dict{String, Any}) → tss::TimeSteppingStrategy
```

辞書から新しい [`TimeSteppingStrategy`](@ref) を作成します。この関数は、すべてのフィールドをキーワード引数として受け入れるコンストラクタを提供する `TimeSteppingStrategy` のすべてのサブタイプに使用できます。

`TimeSteppingStrategy` の型は `dict["tssType"]` の値から解析されます。この文字列で指定された型パラメータは破棄されることに注意してください。したがって、他のフィールドの値から推測可能である必要があります。

型の解析には [`reconstruct_subtype`](@ref) を使用して、`TimeSteppingStrategy` の下のツリーのすべての具体的な葉を見つけます。
