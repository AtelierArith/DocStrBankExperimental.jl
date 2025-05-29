```julia
set!(
    model::SpeedyWeather.AbstractModel;
    orography,
    land_sea_mask,
    kwargs...
)

```

`model`の境界条件フィールドを設定します。入力は、他の`set!`関数と同様に、関数、`RingGrid`、`LowerTriangularMatrix`、またはスカラーであることができます。キーワード`add==true`の場合、入力は既存のフィールドに追加されます。
