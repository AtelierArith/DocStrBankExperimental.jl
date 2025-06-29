```
p4est_iter_corner_side
```

フォレストのコーナーの一つの側面に関する情報。*quad*がローカルである場合（*is_ghost*がfalseの場合）、その*quadid*はツリーの象限配列をインデックスします。それ以外の場合は、ゴースト配列をインデックスします。象限が存在する必要があるが、ゴースト層に含まれていない場合、quad = NULL、is_ghostはtrue、quadid = -1になります。

*faces*フィールドは、ローカルトポロジーに関する追加情報を提供します：もしside[i]->faces[j] == side[k]->faces[l]であれば、これはコーナーのこれら二つの側面の間に共通の面があることを示します。

| フィールド    | 注釈                        |
|:-------- |:------------------------- |
| treeid   | *quad*を含むツリー              |
| corner   | このコーナーに接触する象限のコーナー        |
| is_ghost | ブール値：ローカル (0) またはゴースト (1) |
| quadid   | ツリーまたはゴースト配列のインデックス       |
| faces    | 内部作業データ                   |
