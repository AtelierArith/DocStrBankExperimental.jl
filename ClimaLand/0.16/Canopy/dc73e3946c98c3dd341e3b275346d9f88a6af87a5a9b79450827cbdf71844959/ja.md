```
initialize_auxiliary(
    model::CanopyModel{FT},
    coords,
) where {FT}
```

`CanopyModel`の補助状態ベクトルを作成し、それをClimaCore.Fields.FieldVectorとして返します。

入力の`coords`は通常、ClimaCore Fieldオブジェクトです。

この関数は`CanopyModel`のコンポーネントをループし、各コンポーネントモデルの補助状態ベクトルをコンポーネント名によって構造化された単一の状態ベクトルに追加します。
