```
initialize_prognostic(
    model::CanopyModel{FT},
    coords,
) where {FT}
```

`CanopyModel`の予測状態ベクトルを作成し、それをClimaCore.Fields.FieldVectorとして返します。

入力の`state`は通常、ClimaCore Fieldオブジェクトです。

この関数は`CanopyModel`のコンポーネントをループし、各コンポーネントモデルの予測状態ベクトルをコンポーネント名で構造化された単一の状態ベクトルに追加します。
