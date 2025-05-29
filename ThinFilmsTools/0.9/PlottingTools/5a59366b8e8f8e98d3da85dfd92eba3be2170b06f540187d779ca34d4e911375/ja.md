```
特定の波長（通常はλ0）での多層構造の屈折率をプロットします。

    plot(RIprofile(),
         solution;
         wave=:b, λ=solution.Misc.λ0, θ=solution.Beam.θ[1], s=(640,480),
    )
    gui()

        solution: TMMOpticsからの構造ソリューション
            wave = :b（両方、デフォルト）、:p（p波）、:s（s波）EMFの重なり
            θ: EMFを重ねるための角度、デフォルトでは最初のものが取られます
            λ: EMFを重ねるための波長、デフォルトでは基準のものが取られます
            s: 図のサイズ
```
