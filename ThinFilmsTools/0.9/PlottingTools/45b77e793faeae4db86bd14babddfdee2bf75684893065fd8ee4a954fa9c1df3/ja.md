```
SpaceSolutionRef2DおよびSpaceSolutionTra2Dから得られた目的関数の誤差をプロットします。

    plot(SpaceSolution(),
            x1, x2, S;
            lims=[x1[1], x1[end], x2[1], x2[end]], num_levels=80, s=(640,480)
    )
    gui()

        x1: 第一次元の範囲
        x2: 第二次元の範囲
        S: 目的関数の値を持つ行列
        オプション:
            lims: 2つの軸の制限
            num_levels: 等高線プロットのレベル数
            s: 図のサイズ
```
