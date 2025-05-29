```julia
temperature_equation(
;
    Pr,
    Ra,
    Ge,
    dodissipation,
    boundary_conditions,
    gdir,
    nondim_type
)

```

温度方程のセットアップを作成します（名前付きタプルに格納されます）。

この方程式は、3つの無次元数（プラントル数、レイリー数、ゲバルト数）によってパラメータ化されており、`temperature` フィールドのために別々の境界条件が必要です。`gdir` キーワードは重力の方向を指定し、`non_dim_type` は無次元化のタイプを指定します。
