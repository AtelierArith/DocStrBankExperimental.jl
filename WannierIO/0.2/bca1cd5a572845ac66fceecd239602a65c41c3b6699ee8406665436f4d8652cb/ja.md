```
write_win(filename, params; header)
write_win(filename, params, ::Wannier90Text; header)
write_win(filename, params, ::Wannier90Toml; header)
write_win(filename; header, params...)
write_win(filename, ::Wannier90Text; header, params...)
write_win(filename, ::Wannier90Toml; header, params...)
```

wannier90の`win`ファイルに入力パラメータを書き込みます。

入力パラメータを渡す方法は2つあります：

1. `params`引数に`Dict`（または順序を保持するための`OrderedDict`）として渡す
2. 引数名がwannier90の入力パラメータと同じであるキーワード引数`params...`として渡す

# 例

```julia
using WannierIO

# `Dict`または`OrderedDict`を使用することもできます
params = (;
    num_wann=4,
    num_bands=4,
    # unit_cell_cartは行列で、その列はオングストローム単位の格子ベクトルです
    unit_cell_cart=[
        0.0      2.71527  2.71527
        2.71527  0.0      2.71527
        2.71527  2.71527  0.0
    ],
    # atoms_fracは原子ラベルと分数座標のペアのベクトルです
    atoms_frac=[
        :Si => [0.0, 0.0, 0.0],
        :Si => [0.25, 0.25, 0.25],
        # `:Si`と`"Si"`の両方が許可されています
        # "Si" => [0.25, 0.25, 0.25],
    ],
    # projectionsの各要素はwinファイルの行として書き込まれます
    projections=[
        "random",
    ]
    kpoint_path=[
        [:G => [0.0, 0.0, 0.0], :X => [0.5, 0.0, 0.5]],
        [:X => [0.5, 0.0, 0.5], :U => [0.625, 0.25, 0.625]],
    ],
    mp_grid=[2, 2, 2],
    # kpointsは行列で、その列は分数座標です
    kpoints=[
        [0.0, 0.0, 0.0],
        [0.0, 0.0, 0.5],
        [0.0, 0.5, 0.0],
        [0.0, 0.5, 0.5],
        [0.5, 0.0, 0.0],
        [0.5, 0.0, 0.5],
        [0.5, 0.5, 0.0],
        [0.5, 0.5, 0.5],
    ],
    # 追加のパラメータはキーワード引数として渡すことができます。例：
    num_iter=500,
)
write_win("silicon.win", params)
```
