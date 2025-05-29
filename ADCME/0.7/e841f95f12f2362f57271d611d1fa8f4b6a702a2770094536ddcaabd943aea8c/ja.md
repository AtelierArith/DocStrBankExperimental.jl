```
mutable struct mpi_SparseTensor
    rows::PyObject 
    ncols::PyObject
    cols::PyObject 
    values::PyObject 
    ilower::Int64 
    iupper::Int64 
    N::Int64
    oplibpath::String
end
```

スパース行列のローカルデータを保持するための構造体です。グローバル行列は $M\times N$ の正方行列であると仮定します。現在のプロセッサは `ilower` から `iupper` まで（両端を含む）の行を所有しています。データは以下のように指定されます。

  * `rows`: 非ゼロ値を含む行を示す配列。`rows ≥ ilower` に注意してください。
  * `ncols`: `rows` の各行に対する非ゼロ値の数を示す配列。
  * `cols`: 非ゼロ値の列インデックス。長さは $\sum_{i=1}^{\mathrm{ncols}} \mathrm{ncols}_i$ です。
  * `vals`: `cols` の各列インデックスに対応する非ゼロ値。
  * `oplibpath`: バックエンドライブラリ（`ADCME.load_plugin_MPITensor` によって返される）

すべてのデータ構造は0ベースです。線形ソルバーを使用する場合、$M=N$ に注意してください。

例えば、次のスパース行列を考えます。

```
[  1 0 0 1  ]
[  0 1 2 1  ]
```

次のようになります。

```julia
rows = Int32[0;1]
ncols = Int32[2;3]
cols = Int32[0;3;1,2,3]
values = [1.;1.;1.;2.;1.]
iupper = ilower + 2
```
