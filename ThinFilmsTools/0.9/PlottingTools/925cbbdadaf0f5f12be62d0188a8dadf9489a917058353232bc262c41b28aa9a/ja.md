```
フォトニック結晶構造のフォトニック分散（ブロッホ波ベクトル）をプロットします。
周波数（波長）の範囲と入射角の範囲に対して計算されます。

    plot(PBGDispersion2Dalt(), solution.Bloch; s=(640,480), num_levels=90)
    gui()

        solution: TMMOpticsからのソリューション構造
            s: 図のサイズ
```
