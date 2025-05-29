この構造体は3Dの木間接続情報を保持します。任意の面、エッジ、コーナーの識別が可能です。

配列 tree*to** は z 順序で格納されています。コーナーの場合、zyx に対する順序は 000 001 010 011 100 101 110 111 です。面の場合、順序は -x +x -y +y -z +z です。これらは [0][0]..[0][N-1]..[num*trees-1][0]..[num*trees-1][N-1] に割り当てられます。ここで N は木と面の場合は 6、コーナーの場合は 8、エッジの場合は 12 です。

tree*to*face の値は 0..23 で、ttf % 6 が面番号を、ttf / 6 が面の向きコードを示します。向きは次のように決定されます。my*face と other*face を 0..5 の接続する木の2つの面番号とします。次に、my*face と other*face のうち低い方の最初の面コーナーが、高い方の my*face と other*face の面コーナー番号 0..3 に接続します。この番号が面の向きとして定義されます。my*face == other*face の場合、どちらの面を低い方として扱っても同じ結果になります。

num*vertices を 0 と指定することは有効です。この場合、vertices と tree*to*vertex は NULL に設定されます。そうでない場合、頂点座標は配列 vertices に [0][0]..[0][2]..[num*vertices-1][0]..[num_vertices-1][2] として格納されます。

エッジは木を接続する場合のみ格納されます。この場合、tree*to*edge は *ett_offset* にインデックスします。そうでない場合、tree*to*edge のエントリは -1 でなければならず、このエッジは無視されます。num*edges == 0 の場合、tree*to*edge と edge*to_* 配列は NULL に設定されます。

配列 edge*to** はエッジごとに可変数のエントリを格納します。エッジ e の場合、これらは位置 [ett*offset[e]]..[ett*offset[e+1]-1] にあります。エッジ e のエントリ数は ett*offset[e+1] - ett*offset[e] です。エントリはエッジ e に隣接するすべての木をエンコードします。edge*to** 配列のサイズは num*ett = ett*offset[num*edges] です。edge*to_edge 配列は 0..23 の値を保持し、下位 12 ビットは1つのエッジの向きを示し、上位 12 ビットは反対のエッジの向きを示します。

コーナーは木を接続する場合のみ格納されます。この場合、tree*to*corner は *ctt_offset* にインデックスします。そうでない場合、tree*to*corner のエントリは -1 でなければならず、このコーナーは無視されます。num*corners == 0 の場合、tree*to*corner と corner*to_* 配列は NULL に設定されます。

配列 corner*to** はコーナーごとに可変数のエントリを格納します。コーナー c の場合、これらは位置 [ctt*offset[c]]..[ctt*offset[c+1]-1] にあります。コーナー c のエントリ数は ctt*offset[c+1] - ctt*offset[c] です。エントリはコーナー c に隣接するすべての木をエンコードします。corner*to** 配列のサイズは num*ctt = ctt*offset[num_corners] です。

**to*attr 配列はユーザーによって定義された任意の内容を持つことができます。
