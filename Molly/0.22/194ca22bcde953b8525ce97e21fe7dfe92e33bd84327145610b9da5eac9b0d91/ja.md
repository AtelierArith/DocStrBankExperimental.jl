```
TrajectoryWriter(n_steps, filepath; format="", atom_inds=[],
                 write_velocities=false)
```

シミュレーション中に3D構造をファイルに書き込みます。

Chemfiles.jlを使用して、DCD、XTC、CIF、MOL2、SDF、TRR、XYZなどのさまざまな形式のいずれかに書き込みます。ファイル形式の完全なリストは、[Chemfiles docs](https://chemfiles.org/chemfiles/latest/formats.html#list-of-supported-formats)で確認できます。デフォルトでは、形式はファイル拡張子から推測されますが、文字列として指定することもできます。例：`format="DCD"`。

書き込む原子のインデックスは、リストまたは範囲として`atom_inds`に指定できます。デフォルトではすべての原子が書き込まれます。座標に加えて速度も書き込むことができ、`write_velocities=true`を設定します。ただし、Chemfilesはすべてのファイル形式に速度を書き込むことをサポートしていません。

[`System`](@ref)は`atoms_data`が定義されている必要があり、結合情報が必要な場合は`topology`も必要です。ファイルは追記されるため、シミュレーションの前に既に存在する場合は削除する必要があります。

2Dシステムとは互換性がありません。
