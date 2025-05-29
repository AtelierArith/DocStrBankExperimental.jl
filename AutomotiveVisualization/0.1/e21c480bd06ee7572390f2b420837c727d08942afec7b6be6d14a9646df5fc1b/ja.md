レンダーモデルに命令を追加します

入力:     rendermodel   - 命令を追加するRenderModel     f             - 呼び出す関数、最初の引数はCairoContextでなければなりません     args          - fへの入力引数のタプル、CairoContextをスキップ     coordinate*system - 座標が与えられる座標系（:scene, :camera*pixels, :camera*relativeのいずれか）       `:scene` - 座標は世界フレームの物理座標で、単位は[メートル]       `:camera*pixels`- 座標はピクセル単位で、カメラによって選択された矩形に対して相対的です（単位は[ピクセル]）`:camera_relative` - 座標はカメラによって選択された矩形の範囲0から1のパーセンテージです

例: add*instruction!(rendermodel, render*text, ("hello world", 10, 20, 15, [1.0,1.0,1.0]))
