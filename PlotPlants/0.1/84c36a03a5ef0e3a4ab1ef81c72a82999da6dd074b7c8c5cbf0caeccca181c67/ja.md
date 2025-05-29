```
plot_hexbin!(
            ax::PyObject,
            xs::Array,
            ys::Array;
            cmap::String = "Greys",
            logbins::Bool = false,
            gridsize::Number = 25
)
plot_hexbin!(
            ax::PyObject,
            xs::Array,
            ys::Array,
            xlims::Array,
            ylims::Array;
            cmap::String = "Greys",
            logbins::Bool = false,
            gridsize::Number = 25
)
```

軸に密度プロットを描画します。

  * `ax` 描画する軸
  * `xs` Xの配列
  * `ys` Yの配列
  * `cmap` オプション。カラーマップスキーム
  * `logbins` オプション。trueの場合、ビンの色付けにlog(count)を使用
  * `gridsize` 両方向のビンの数
  * `xlim` x軸の制限。サブプロット間でプロット領域を等しくするために使用
  * `ylim` y軸の制限。サブプロット間でプロット領域を等しくするために使用
