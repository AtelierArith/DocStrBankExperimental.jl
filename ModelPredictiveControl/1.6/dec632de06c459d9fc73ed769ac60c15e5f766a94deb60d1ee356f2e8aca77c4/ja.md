```
default_nint(model::SimModel, i_ym=1:model.ny, nint_u=0)
```

デフォルトでは、`model`が[`LinModel`](@ref)でない場合、各測定出力に1つの積分器があります。

拡張されたモデルが観測可能であることの検証はありません。操作された入力ごとの積分器の量が`nint_u ≠ 0`の場合、メソッドは各測定出力にゼロの積分器を返します。
