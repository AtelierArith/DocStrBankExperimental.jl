```
p4est_connectivity
```

この構造体は2Dの木間接続情報を保持します。任意の面やコーナーの識別が可能です。

配列 tree*to** は z 順序で格納されています。コーナーの場合、yx に対する順序は 00 01 10 11 です。面の場合、順序は -x +x -y +y です。これらは [0][0]..[0][3]..[num*trees-1][0]..[num*trees-1][3] に割り当てられます。

tree*to*face の値は 0..7 で、ttf % 4 が面番号を、ttf / 4 が面の向きコードを示します。向きは、z 順序に整列したエッジの場合は 0、z 順序に逆に走るエッジの場合は 1 です。

num*vertices を 0 と指定することは有効です。この場合、vertices と tree*to*vertex は NULL に設定されます。それ以外の場合、頂点座標は配列 vertices に [0][0]..[0][2]..[num*vertices-1][0]..[num_vertices-1][2] として格納されます。

コーナーは、木を接続する場合にのみ保存されます。この場合、tree*to*corner は *ctt_offset* にインデックスします。それ以外の場合、tree*to*corner のエントリは -1 であり、このコーナーは無視されます。num*corners == 0 の場合、tree*to*corner と corner*to_* 配列は NULL に設定されます。

配列 corner*to** は、コーナーごとに可変数のエントリを格納します。コーナー c の場合、これらは位置 [ctt*offset[c]]..[ctt*offset[c+1]-1] にあります。コーナー c のエントリ数は ctt*offset[c+1] - ctt*offset[c] です。エントリはコーナー c に隣接するすべての木をエンコードします。corner*to** 配列のサイズは num*ctt = ctt*offset[num_corners] です。

**to*attr 配列は、ユーザーによって定義された任意の内容を持つことができます。

| フィールド            | 注釈                                                     |
|:---------------- |:------------------------------------------------------ |
| num_vertices     | 森の*埋め込み*を定義する頂点の数（トポロジーではない）                           |
| num_trees        | 木の数                                                    |
| num_corners      | トポロジーを定義するのに役立つコーナーの数                                  |
| vertices         | サイズ (3 * *num_vertices*) の配列                           |
| tree*to*vertex   | 各木を `c++ R^3` に埋め込む（例：可視化のため、p4est_vtk.h を参照）          |
| tree*attr*bytes  | tree*to*attr における木ごとのバイト数                              |
| tree*to*attr     | `p4est` によって触れられない                                     |
| tree*to*tree     | (4 * *num_trees*) 面を越えた隣接木                             |
| tree*to*face     | (4 * *num_trees*) 面と面+向き（説明を参照）                        |
| tree*to*corner   | (4 * *num_trees*) または NULL（説明を参照）                      |
| ctt_offset       | *corner*to*tree* および *corner*to*corner* におけるコーナーのオフセット |
| corner*to*tree   | コーナーで出会う木のリスト                                          |
| corner*to*corner | コーナーで出会う木のコーナーのリスト                                     |
