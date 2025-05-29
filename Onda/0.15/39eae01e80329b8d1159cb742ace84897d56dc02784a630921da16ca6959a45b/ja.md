```
@version MergedAnnotationV1 > AnnotationV1 begin
    from::Vector{UUID}
end
```

「マージ」された1つ以上の既存の注釈から派生した注釈を表すLegolas生成のレコードタイプです。

このレコードタイプは、注釈のソース注釈の`id`をエントリとする単一の追加必須フィールド`from::Vector{UUID}`で`AnnotationV1`を拡張します。

Legolasレコードタイプに関する詳細は、https://github.com/beacon-biosignals/Legolas.jl を参照してください。
