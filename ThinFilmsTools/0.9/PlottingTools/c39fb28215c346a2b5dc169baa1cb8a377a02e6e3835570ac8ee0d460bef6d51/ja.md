```
フォトニック結晶構造のフォトニック分散（ブロッホ波ベクトル）をプロットし、
周波数（波長）の範囲と入射角の範囲に対して計算されます。

この関数は、偏光タイプのうちの1つのブロッホ波ベクトルをプロットします。

    plot(PBGDispersion2D(), solution.Bloch; wave=:p, s=(640,480), num_levels=90)
    gui()

        solution.Bloch: TMMOpticsからのsolution.Bloch構造
            wave: :p（p波、デフォルト）または:s（s波）のいずれか
            s: 図のサイズ
```
